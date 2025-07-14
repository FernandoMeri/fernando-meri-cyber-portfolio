# Apply filters to SQL queries

## Project description

In this project, I act as a security professional within a large organization, tasked with investigating potential security issues related to employee login attempts and machine activities. My objective is to apply various SQL filters on the `employees` and `log_in_attempts` tables to retrieve specific data sets. This will demonstrate my expertise in using SQL operators like `AND`, `OR`, and `NOT` for effective data analysis in cybersecurity investigations.

## Retrieve after hours failed login attempts

This query identifies failed login attempts that occurred outside of normal working hours (after 18:00). This is crucial for security, as these events could indicate brute force attempts, unauthorized access, or suspicious activity by internal users attempting to circumvent regular monitoring. The query uses the `AND` operator to combine the login failure condition with the specific time condition.

`SQL`

`SELECT`  
    `event_id,`  
    `username,`  
    `login_date,`  
    `login_time,`  
    `country,`  
    `ip_address,`  
    `success`  
`FROM`  
    `log_in_attempts`  
`WHERE`  
    `success = FALSE`  
    `AND login_time > '18:00:00';`

## Retrieve login attempts on specific dates

This query retrieves all login attempts that occurred on specific dates (2022-05-09 or 2022-05-08). Filtering by specific dates is critical in incident response and forensic analysis, as it allows security analysts to focus on activity within a known suspicious time frame. The `OR` operator is used to include records from either of the two specified dates.

`SQL`

`SELECT`  
    `event_id,`  
    `username,`  
    `login_date,`  
    `login_time,`  
    `country,`  
    `ip_address`  
`FROM`  
    `log_in_attempts`  
`WHERE`  
    `login_date = '2022-05-09'`  
    `OR login_date = '2022-05-08';`

## Retrieve login attempts outside of Mexico

This query identifies login attempts that did not originate in Mexico. It is vital for filtering out noise and focusing the investigation on external threats or unusual activity coming from unexpected geographic locations. The `NOT LIKE` operator is used together with the % wildcard to ensure that all variations of ‘Mexico’ (such as ‘MEX’ or ‘MEXICO’) in the country column are excluded.

`SQL`

`SELECT`  
    `event_id,`  
    `username,`  
    `login_date,`  
    `login_time,`  
    `country,`  
    `ip_address,`  
    `success`  
`FROM`  
    `log_in_attempts`  
`WHERE`  
    `country NOT LIKE '%MEX%';`

## Retrieve employees in Marketing

This query identifies employees in the Marketing department who work in any of the 'East' offices. This is crucial for targeted security updates or policy implementations for specific departmental and location-based groups. The `AND` operator ensures both conditions must be met for an employee to be included in the results.

`SQL`

`SELECT`  
    `employee_id,`  
    `username,`  
    `department,`  
    `office`  
`FROM`  
    `employees`  
`WHERE`  
    `department = 'Marketing'`  
    `AND office LIKE 'East%';`

## Retrieve employees in Finance or Sales

## This query retrieves all employees belonging to either the Finance or Sales departments. Using the OR operator allows for a broader selection of employees across multiple relevant departments, enabling specific security updates or training initiatives that apply to more than one business unit.

`SQL`

`SELECT`  
    `employee_id,`  
    `username,`  
    `department,`  
    `office`  
`FROM`  
    `employees`  
`WHERE`  
    `department = 'Finance'`  
    `OR department = 'Sales';`

## Retrieve all employees not in IT

This query identifies all employees who are not part of the 'Information Technology' department. The `NOT` operator is used to exclude employees from a specific group who have already received an update, ensuring that the remaining employees receive necessary security updates or communications.

`SQL`

`SELECT`  
    `employee_id,`  
    `username,`  
    `department,`  
    `office`  
`FROM`  
    `employees`  
`WHERE`  
    `department NOT LIKE 'Information Technology';`

## Summary

In this project, I demonstrated my proficiency in SQL filtering by analyzing a security scenario involving employee logins and machine data. I crafted and explained various SQL queries using `AND`, `OR,` and `NOT` operators to identify suspicious activities and target specific employee groups for security actions. This exercise highlights my ability to leverage SQL as a vital tool for data investigation and maintaining organizational security.  
