/* 
   Project: Employee Data Cleaning & Analysis
   Tool: MySQL
   Database: human_research_schema
   Table: human_resources
*/

-- Preview data
SELECT * FROM human_research_schema.human_resources;


-- 1. DATA EXPLORATION & INITIAL INSPECTION ===============================================================
DESCRIBE human_resources;


-- 2. DATA CLEANING & TRANSFORMATION ======================================================================

-- Rename incorrect / inconsistent columns
ALTER TABLE human_resources
CHANGE COLUMN ï»¿id emp_id VARCHAR(20) NULL;

-- Standardize date columns to DATE data type
ALTER TABLE human_resources
MODIFY COLUMN birthdate DATE,
MODIFY COLUMN hire_date DATE,
MODIFY COLUMN termdate DATE;

-- Clean and format birthdate column
UPDATE human_resources
SET birthdate = 
CASE
    WHEN birthdate LIKE '%/%' THEN DATE_FORMAT(STR_TO_DATE(birthdate, '%m/%d/%Y'), '%Y-%m-%d')
    WHEN birthdate LIKE '%-%' THEN DATE_FORMAT(STR_TO_DATE(birthdate, '%m-%d-%Y'), '%Y-%m-%d')
    ELSE NULL
END;

-- Clean and format hire_date column
UPDATE human_resources
SET hire_date = 
CASE
    WHEN hire_date LIKE '%/%' THEN DATE_FORMAT(STR_TO_DATE(hire_date, '%m/%d/%Y'), '%Y-%m-%d')
    WHEN hire_date LIKE '%-%' THEN DATE_FORMAT(STR_TO_DATE(hire_date, '%m-%d-%Y'), '%Y-%m-%d')
    ELSE NULL
END;

-- Clean and format termdate column
UPDATE human_resources
SET termdate = DATE(STR_TO_DATE(termdate, '%Y-%m-%d %H:%i:%s UTC'))
WHERE termdate IS NOT NULL AND termdate != '';


-- Add and calculate AGE column
ALTER TABLE human_resources
ADD COLUMN age INT;

UPDATE human_resources
SET age = TIMESTAMPDIFF(YEAR, birthdate, CURDATE());

-- Validate age logic
SELECT birthdate, age 
FROM human_resources
WHERE age < 0;

SELECT MIN(age) AS youngest, MAX(age) AS oldest
FROM human_resources;


-- 3. EXPLORATORY DATA ANALYSIS (EDA) ===============================================================

-- Gender distribution (active employees)
SELECT gender, COUNT(*) AS count
FROM human_resources
WHERE termdate IS NULL
GROUP BY gender;

-- Race distribution
SELECT race, COUNT(*) AS count
FROM human_resources
WHERE termdate IS NULL
GROUP BY race
ORDER BY count DESC;

-- Age distribution overview
SELECT MIN(age) AS youngest, MAX(age) AS oldest
FROM human_resources
WHERE termdate IS NULL;

-- Age group breakdown
SELECT
    CASE
        WHEN age BETWEEN 18 AND 24 THEN '18-24'
        WHEN age BETWEEN 25 AND 34 THEN '25-34'
        WHEN age BETWEEN 35 AND 44 THEN '35-44'
        WHEN age BETWEEN 45 AND 54 THEN '45-54'
        WHEN age BETWEEN 55 AND 64 THEN '55-64'
        ELSE '65+'
    END AS age_group,
    COUNT(*) AS count
FROM human_resources
WHERE termdate IS NULL
GROUP BY age_group
ORDER BY age_group;

-- Age group by gender
SELECT
    CASE
        WHEN age BETWEEN 18 AND 24 THEN '18-24'
        WHEN age BETWEEN 25 AND 34 THEN '25-34'
        WHEN age BETWEEN 35 AND 44 THEN '35-44'
        WHEN age BETWEEN 45 AND 54 THEN '45-54'
        WHEN age BETWEEN 55 AND 64 THEN '55-64'
        ELSE '65+'
    END AS age_group,
    gender,
    COUNT(*) AS count
FROM human_resources
WHERE age >= 18 AND termdate IS NULL
GROUP BY age_group, gender
ORDER BY age_group, gender;

-- Headquarters vs. Remote employees
SELECT location, COUNT(*) AS count_location
FROM human_resources
WHERE termdate IS NULL 
GROUP BY location
ORDER BY location;

-- Average length of employment (terminated employees)
SELECT ROUND(AVG(DATEDIFF(termdate, hire_date) / 365), 0) AS avg_length_employment
FROM human_resources
WHERE termdate <= CURDATE() AND termdate IS NOT NULL;

-- Gender distribution by department
SELECT department, gender, COUNT(*) AS count
FROM human_resources
WHERE termdate IS NULL
GROUP BY department, gender
ORDER BY department;

-- Job title distribution
SELECT jobtitle, COUNT(*) AS count
FROM human_resources
WHERE termdate IS NULL
GROUP BY jobtitle
ORDER BY count DESC;

-- Department turnover rate
SELECT 
    department,
    total_count,
    terminated_count,
    ROUND((terminated_count / total_count) * 100, 2) AS termination_rate
FROM (
    SELECT
        department,
        COUNT(*) AS total_count,
        SUM(CASE WHEN termdate IS NOT NULL AND termdate <= CURDATE() THEN 1 ELSE 0 END) AS terminated_count
    FROM human_resources
    GROUP BY department
) AS subquery
ORDER BY termination_rate DESC;

-- Distribution of employees across locations (by state)
SELECT location_state, COUNT(*) AS count
FROM human_resources
WHERE termdate IS NULL
GROUP BY location_state
ORDER BY count DESC;

-- Employee count trend over time (hires vs terminations)
SELECT 
    year,
    hires,
    terminations,
    hires - terminations AS net_change,
    ROUND(((hires - terminations) / hires) * 100, 2) AS net_change_percent
FROM (
    SELECT
        YEAR(hire_date) AS year,
        COUNT(*) AS hires,
        SUM(CASE WHEN termdate IS NOT NULL AND termdate <= CURDATE() THEN 1 ELSE 0 END) AS terminations
    FROM human_resources
    GROUP BY YEAR(hire_date)
) AS subquery
ORDER BY year ASC;

-- Average tenure by department
SELECT department, ROUND(AVG(DATEDIFF(termdate, hire_date) / 365), 0) AS avg_tenure
FROM human_resources
WHERE termdate IS NOT NULL AND termdate <= CURDATE()
GROUP BY department;

-- Check unique states
SELECT DISTINCT(location_state) FROM human_resources;
