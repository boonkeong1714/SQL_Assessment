# SQL Assessment: Codecademy Learners Mockup Data
  
## Answers

2.
* What are the Top 25 schools (.edu domains)?
```SQL
SELECT 
	email_domain AS "Top 25 schools (.edu domains)", 
	COUNT(DISTINCT user_id) AS "Amount"

FROM users
	WHERE (email_domain LIKE "%edu")

GROUP BY 1
ORDER BY 2 DESC
LIMIT 25;
```

![Query Results 2a](https://raw.githubusercontent.com/boonkeong1714/SQL_Assessment/main/2a.jpg)

* How many .edu learners are located in New York?

```SQL
SELECT 
	COUNT(user_id) AS "How many .edu learners are located in New York?"

FROM users
	WHERE (city = "New York") AND (email_domain LIKE "%edu");
```

![Query Results 2a](https://raw.githubusercontent.com/boonkeong1714/SQL_Assessment/main/2b.jpg)


* How many of these Codecademy learners are using the mobile app?

```SQL
SELECT 
	COUNT(user_id) AS "How many of these Codecademy learners are using the mobile app?"

FROM users
	WHERE (mobile_app = "mobile-user");
```

![Query Results 2a](https://raw.githubusercontent.com/boonkeong1714/SQL_Assessment/main/2c.jpg)

3. query for the sign up counts for each hour.

```SQL
-- display top 20 signup rank hour --
SELECT 
	strftime("%Y-%m-%d %Hhr", sign_up_at) AS "Hour",
   	count(strftime("%H", sign_up_at)) AS "Sign up counts for each hour"

FROM users

GROUP BY 1
ORDER BY 2 DESC
LIMIT 20;
```

![Query Results 2a](https://raw.githubusercontent.com/boonkeong1714/SQL_Assessment/main/3.jpg)


4.
• Do different schools (.edu domains) prefer different courses?

```SQL
SELECT 
  email_domain AS School,
	SUM(CASE 
          WHEN learn_cpp = "started" THEN 1 
          WHEN learn_cpp = "completed" THEN 1 ELSE 0 END) AS "C++",
	SUM(CASE 
          WHEN learn_sql = "started" THEN 1 
          WHEN learn_sql = "completed" THEN 1 ELSE 0 END) AS "SQL",
	SUM(CASE 
          WHEN learn_html = "started" THEN 1 
          WHEN learn_html = "completed" THEN 1 ELSE 0 END) AS "HTML",
	SUM(CASE 
          WHEN learn_javascript = "started" THEN 1 
          WHEN learn_javascript = "completed" THEN 1 ELSE 0 END) AS "JavaScript",
	SUM(CASE 
          WHEN learn_java = "started" THEN 1 
          WHEN learn_java = "completed" THEN 1 ELSE 0 END) AS "Java",
  COUNT(email_domain) AS "Total"

FROM users 
	LEFT JOIN progress ON users.user_id = progress.user_id

GROUP BY email_domain
ORDER BY COUNT(email_domain) DESC
LIMIT 25;
```

![Query Results 2a](https://raw.githubusercontent.com/boonkeong1714/SQL_Assessment/main/4a.jpg)

• What courses are the New Yorkers students taking?

```SQL
SELECT 
	SUM(CASE WHEN learn_cpp = "started" THEN 1 
           WHEN learn_cpp = "completed" THEN 1 ELSE 0 END) "C++",
	SUM(CASE WHEN learn_sql = "started" THEN 1 
           WHEN learn_sql = "completed" THEN 1 ELSE 0 END) "SQL",
	SUM(CASE WHEN learn_html = "started" THEN 1 
           WHEN learn_html = "completed" THEN 1 ELSE 0 END) "HTML",
	SUM(CASE WHEN learn_javascript = "started" THEN 1 
           WHEN learn_javascript = "completed" THEN 1 ELSE 0 END) "JavaScript",
	SUM(CASE WHEN learn_java = "started" THEN 1 
           WHEN learn_java = "completed" THEN 1 ELSE 0 END) "Java"

FROM users 
	LEFT JOIN progress ON users.user_id = progress.user_id

WHERE city = "New York"
GROUP BY city;
```

![Query Results 2a](https://raw.githubusercontent.com/boonkeong1714/SQL_Assessment/main/4b.jpg)

• What courses are the Chicago students taking?

```SQL
SELECT 
	SUM(CASE WHEN learn_cpp = "started" THEN 1 
           WHEN learn_cpp = "completed" THEN 1 ELSE 0 END) "C++",
	SUM(CASE WHEN learn_sql = "started" THEN 1 
           WHEN learn_sql = "completed" THEN 1 ELSE 0 END) "SQL",
	SUM(CASE WHEN learn_html = "started" THEN 1 
           WHEN learn_html = "completed" THEN 1 ELSE 0 END) "HTML",
	SUM(CASE WHEN learn_javascript = "started" THEN 1 
           WHEN learn_javascript = "completed" THEN 1 ELSE 0 END) "JavaScript",
	SUM(CASE WHEN learn_java = "started" THEN 1 
           WHEN learn_java = "completed" THEN 1 ELSE 0 END) "Java"

FROM users 
	LEFT JOIN progress ON users.user_id = progress.user_id

WHERE city = "Chicago"
GROUP BY city;
```

![Query Results 2a](https://raw.githubusercontent.com/boonkeong1714/SQL_Assessment/main/4c.jpg)

-----

**===== Reflection Questions =====**  

1. What did you like about this project?
..It is like treausre hunting, using SQL to nagivate and locate the treasure.

2. What did you struggle with in this project?
..* Tried to count how many NULL, which is quite tricky to do.
..* Deal with slightly big amount(>500) of data is quite overwhelming.

3. What would make your experience with this assessment better?
to learn SQL better we need to do a lot of exercise,
Analyze Data SQL in codeacademy


-----
