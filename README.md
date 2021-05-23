# SQL Assessment: Codecademy Learners Mockup Data

2.
• What are the Top 25 schools (.edu domains)?

SELECT 
	email_domain AS "Top 25 schools (.edu domains)", 
	COUNT(DISTINCT user_id) AS "Amount"

FROM users
	WHERE (email_domain LIKE "%edu")

GROUP BY 1
ORDER BY 2 DESC
LIMIT 25;


• How many .edu learners are located in New York?

SELECT 
	COUNT(user_id) AS "How many .edu learners are located in New York?"

FROM users
	WHERE (city = "New York") AND (email_domain LIKE "%edu");


• How many of these Codecademy learners are using the mobile app?

SELECT 
	COUNT(user_id) AS "How many of these Codecademy learners are using the mobile app?"

FROM users
	WHERE (mobile_app = "mobile-user");


3. query for the sign up counts for each hour.

-- display top 20 signup rank hour --
SELECT 
	strftime("%Y-%m-%d %Hhr", sign_up_at) AS "Hour",
   	count(strftime("%H", sign_up_at)) AS "Sign up counts for each hour"

FROM users

GROUP BY 1
ORDER BY 2 DESC
LIMIT 20;


4.
• Do different schools (.edu domains) prefer different courses?

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



• What courses are the New Yorkers students taking?

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


• What courses are the Chicago students taking?

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


-----
●  	What did you like about this project?
It is like treausre hunting, using SQL to nagivate and locate the treasure.

●  	What did you struggle with in this project?
Tried to count how many NULL, which is quite tricky to do.
Deal with slightly big amount(>500) of data is quite overwhelming.

●  	What would make your experience with this assessment better?
to learn SQL better we need to do a lot of exercise,
Analyze Data SQL in codeacademy


-----
