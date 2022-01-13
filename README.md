# School District Analysis
Report prepared for Module 4 challenge by Hannah Wikum - January 2022

# Resources
* Data Source: clean_students_complete.csv (provided)
* Software: Python 3.7 Anaconda Development Environment, Jupyter Notebook, Git Bash 2.34.1.windows.1
___

# Overview
## Module
This analysis was performed for Maria, a chief data scientist for a school district. During the module, I prepared standardized test data for 39,170 students across 15 schools in the district by importing a CSV, inspecting the data, and cleaning names before doing a comprehensive analysis. The analysis included:
  * number of students
  * number of schools
  * total  budget
  * average math and reading test scores
  * passing percentages
 The data was further analyzed and presented in data frames by school, school spending/student, school size, and school type. All work was completed in a Jupyter Notebook and committed to this GitHub repository.
 
 ## Challenge
 For the challenge, the school board suspected the math and reading scores for ninth graders at Thomas High School had been altered. I was asked to remove the scores while keeping the remaining data intact to protect the integrity of the standardized testing process. This part of the analysis required two steps:
  1) Replace the math and reading scores for 9th graders at Thomas High School with 'NaN'
  2) Rerun the analysis described above on all remaining data without the impact of the academic dishonesty.
 
## Sample Code

_highlight a few pivotal lines of code that helped with the analysis_

___

# Results
Replacing the math and reading scores for 461 9th graders at Thomas High School had an impact on the summaries I created earlier for the module, albeit relatively small because it represented approximately 1.2% of total students in the disctrict. When you look at descriptive statistics using .describe() on the 9th grade Thomas High School data before it was replaced with NaN, you can see the average reading and math scores were 83.7 and 83.6, respectively. (Note: Student ID was cropped out of the image below because the statistics are not relevant.)

![image](https://user-images.githubusercontent.com/93058069/149419466-7cb4b279-2d1c-4608-a13d-4440a3ffa4ed.png)

Here is the impact to some of the summaries by replacing the data for math and reading scores for 9th graders at Thomas High School with NaN:

_Use a bulleted list to answer the following - include pictures of data frames or tables_
 * **Impact to district summary**
     The only visible change to the district summary is that the average math scores are slightly lower than before. As you can see in the images below, the average math score for the district below was 79.0. The average math score for 9th graders at Thomas was 83.6, so removing them from the data had a negative impact on the average math score for the district. It is also true that 9th graders at Thomas had higher than average reading scores, but the change with removing them was not significant enough when reporting is shown to the tenth decimal. If we had replaced the scores with 0, the averages would have decreased a lot more. The total students number remained the same because we replaced the scores with NaN instead of removing the 461 students from the data.
     
     _District Summary Before_

     ![image](https://user-images.githubusercontent.com/93058069/149420178-f1476d83-1b0b-4ae7-9962-ed27b5cea8de.png)


     _District Summary After Replacing Thomas 9th Grade Math/Reading Scores with NaN_

     ![image](https://user-images.githubusercontent.com/93058069/149420340-e9a4f53e-2f88-45d7-8f10-4d4f92dcb1e0.png)



     
2. Impact to school summary
3. How does replacing the ninth graders' math and reading scores affect Thomas High School's performance relative to the other schools?
4. How does replacing the ninth grade scores affect the following:
5.   math and reading scores by grade
6.   scores by school spending
7.   scores by school size
8.   scores by school type


# Summary
_list the four changes to the school district analysis after reading and math scores have been replaced_
