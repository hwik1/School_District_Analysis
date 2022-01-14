# School District Analysis
Report prepared for Module 4 challenge by Hannah Wikum - January 2022

# Resources
* Data Source: clean_students_complete.csv (provided)
* Software: Python 3.7 Anaconda Development Environment with pandas and numpy, Jupyter Notebook, Git Bash 2.34.1.windows.1
___

# Overview
## Module
This analysis was performed for Maria, a chief data scientist for a school district. During the module, I prepared standardized test data for 39,170 students across 15 schools in the district by importing a CSV, inspecting the data, and cleaning names before doing a comprehensive analysis. The analysis included:
  * number of students
  * number of schools
  * total  budget
  * average math and reading test scores
  * passing percentages
  
 The data was further analyzed and presented in DataFrames by school, school spending/student, school size, and school type. All work was completed in a Jupyter Notebook and committed to this GitHub repository.
 
 ## Challenge
 For the challenge, the school board suspected the math and reading scores for 9th graders at Thomas High School had been altered. I was asked to remove the scores while keeping the remaining data intact to protect the integrity of the standardized testing process. This part of the analysis required two steps:
  1. Replace the math and reading scores for 9th graders at Thomas High School with NaN
  2. Rerun the analysis described above on all remaining data without the impact of the academic dishonesty
 
## Sample Code
To complete this analysis for the module and challenge, I had to learn several new functions.

 1. To get the number of students at Thomas High School in 9th grade (or later on the number in 10th-12th), I needed to select based on conditional operators using == for equal to (like in the example below) or != for not equal to. Here is a sample of the code with two conditions:

`#Step 1. Get the number of students that are in ninth grade at Thomas High School.`

`thomas_ninth_count = school_data_complete_df[(school_data_complete_df["grade"] == "9th") & (school_data_complete_df["school_name"] == "Thomas High School")].count()["Student ID"]`

 2. To replace the recalculated % passing math, % passing reading, and % overall passing for Thomas after replacing 9th grade scores with NaN, I had to use the loc function to find Thomas High School in the index and then the appropriate column. Here is a sample of part of my code:

`#Step 13. Replace the passing reading percentage for Thomas High School in the per_school_summary_df.`

`per_school_summary_df.loc[per_school_summary_df.index == "Thomas High School", "% Passing Reading"] = percentage_passing_reading_thomas`


3. Another bit of code I learned how to use is map and format to update the format. For this analysis, we converted average test scores to one decimal place and showed percentages without decimals. Here is a sample of the code I used to format an average math score column with one decimal place:

`#Format the columns.`

`district_summary_df["Average Math Score"] = district_summary_df["Average Math Score"].map("{:.1f}".format)`
___

# Results
Replacing the math and reading scores for 461 9th graders at Thomas High School had an impact on some of the summaries I created earlier for the module, albeit relatively small because it represented approximately 1.2% of total students in the disctrict. When you look at descriptive statistics using .describe() on the 9th grade Thomas High School data before it was replaced with NaN, you can see the average reading and math scores were 83.7 and 83.6, respectively. (Note: Student ID was cropped out of the image below because the statistics are not relevant.)

![image](https://user-images.githubusercontent.com/93058069/149419466-7cb4b279-2d1c-4608-a13d-4440a3ffa4ed.png)

## Impact to Previous Summaries

 * **Impact to district summary:**
 The only visible change to the district summary is that the average math scores are slightly lower than before. As you can see in the images below, the average math score for the district below was 79.0 and decreased to 78.9. The average math score for 9th graders at Thomas was 83.6, so removing them from the data had a negative impact on the average math score for the district. It is also true that 9th graders at Thomas had higher than average reading scores, but the change with removing them was not significant enough when reporting is shown to the tenth decimal. If we had replaced the scores with 0, the averages would have decreased a lot more. The total students number remained the same because we replaced the scores with NaN instead of removing the 461 students from the data.
     
     _District Summary Before_

     ![image](https://user-images.githubusercontent.com/93058069/149420178-f1476d83-1b0b-4ae7-9962-ed27b5cea8de.png)


     _District Summary After Replacing Thomas 9th Grade Math/Reading Scores with NaN_

     ![image](https://user-images.githubusercontent.com/93058069/149420340-e9a4f53e-2f88-45d7-8f10-4d4f92dcb1e0.png)

 * **Impact to school summary:** The school summary had a more noticeable change for the Thomas High School row because the 461 9th graders made up 28% of the student population at that high school. None of the data changed for other schools, so I chose to show the difference before and after in just the Thomas High School row for space saving purposes. (The full DataFrame can be seen in the PyCitySchool_Challenge jupyter notebook.) Replacing the 9th grade math and reading scores didn't impact the school type, student count, school budget, or per student budget, but did change the results for every other metric. The average math score went down because the average of the 9th grade math score (as seen above) was 83.6, which is higher than the 10-12th grade average. The percentage passing math also went down. Inversely, the average reading score and % passing reading went up. The total overall passing % declined after 9th grade data was removed. 

     _School District Summary Before (only Thomas row shown)_
     
     ![image](https://user-images.githubusercontent.com/93058069/149431830-7ad1986a-7889-4e2d-9656-93566a859b0a.png)

    _School District Summary After Replacing Thomas 9th Grade Math/Reading Scores with NaN (only Thomas row shown)_
     
     ![image](https://user-images.githubusercontent.com/93058069/149433152-31c002e2-300b-4ed6-9371-823ca109d68a.png)

* **Impact on performance compared to other schools:** The overall passing percentage for Thomas dropped 0.32% after taking out the 9th grade math and reading scores, but it still had the second best overall passing rate behind Cabrera High School. Thomas also ranked 5th both before and after in average reading scores, but went from the school with the highest passing reading percentage to third best. The drop in average math scores also impacted Thomas High School compared to the other schools because it went from the school with the fourth best average math scores to 6th. The overall passing math percentage compared to other schools remained the same at 7th both before and after. 

* **Other impacts:** Replacing the 9th grade scores at Thomas High School also impacted several other metrics:
    * **Math and Reading Scores by Grade:** Average math and reading scores only changed for 9th graders at Thomas High School. I replaced the average score for the 9th graders at Thomas High School with NaN, so it could not calculate an average and displayed NaN. No other grade-level or school-level data was changed, as you can see in the pictures below. (Average reading scores by grade are shown, but it was the same for averaeg math scores by grade.)

   _Average Reading Scores by Grade Before_
     
   ![image](https://user-images.githubusercontent.com/93058069/149437389-c1517289-cdce-4773-b4df-b43d56e45bff.png)

   _Average Reading Scores by Grade After_

   ![image](https://user-images.githubusercontent.com/93058069/149437462-3e21b1aa-7b54-4d11-9409-7baa89a1f871.png)

  * **Score by School Spending:** Thomas High School averages $638.00 in spending per student, so it falls into the third spending bin of $630-644. Replacing the scores for 9th graders at Thomas only impacted overall statistics for Thomas, so the $630-644 bin is the only one that would have changed. There are three other schools in the $630-644 spending bin: Figueroa, Ford, and Rodriguez high schools. The change in average reading and math scores and passing percentages was so minor that it did not have an impact on the total spending bin. All five metrics look the same in the before and after images below with the current one decimal (for average math/reading scores) or no decimal (for the percentages) formatting.

   _Average Scores by Spending Bin Before_
   
   ![image](https://user-images.githubusercontent.com/93058069/149437909-6b0e8e79-f403-4879-8732-72d4ed4eec5d.png)

   _Average Scores by Spending Bin After_
   
   ![image](https://user-images.githubusercontent.com/93058069/149438429-3f0aa42f-0578-4235-912b-e548a7a2b13b.png)

  * **Scores by School Size:** With 1635 students, Thomas qualifies as a medium-sized school (1000-2000). There are four other schools in the medium school size bin: Cabrera, Griffin, Shelton, and Wright high schools. The medium school size metrics is the only row that could change, but as with the before/after results for scores by spending bin, there is no change in the before and after average scores displayed in the DataFrames below. The impact of replacing 9th grade scores at Thomas does not show up when looking at average scores to one decimal or passing percentages without a decimal.

    _Average Scores by School Size Before_
    
   ![image](https://user-images.githubusercontent.com/93058069/149439888-41e79bf8-aece-46ec-9652-5b6cf9636020.png)

   _Average Scores by School Size After_
   
   ![image](https://user-images.githubusercontent.com/93058069/149439921-1639fafe-4aab-4465-9790-a242631fac22.png)

  *  **Scores by School Type:** Thomas is one of eight schools in the district that is a charter school, thus replacing data for 9th graders at Thomas could only impact the charter school type row in the before/after analysis. As with the two examples for scores by spending bin or scores by school size bin, there are so many schools/students represented in this data that replacing data for one grade at one school did not impact the results (see below).

    _Average Scores by School Type Before_
    
    ![image](https://user-images.githubusercontent.com/93058069/149440476-e1d293db-12f4-4df6-bcfa-56c136a43778.png)

    _Average Scores by School Type After_
    
    ![image](https://user-images.githubusercontent.com/93058069/149440509-f0394e15-7a21-4279-9b55-f9c32f0fb627.png)
    
 ___
 
# Summary
After replacing the math and reading scores for 9th graders at Thomas High School with NaN, there were a number of changes to the updated school district analysis compared to results of the original analysis performed for the module, including:
   1. At a district level (all schools combined), average math scores decreased from 79.0 to 78.9.
   2. The DataFrames for average math or reading scores by grade now show 'NaN' for 9th graders at Thomas instead of the original average scores (83.6 and 83.7, respectively).
   3. In the School District DataFrame, average math scores at Thomas decreased and average reading scores at Thomas increased slightly.
   4. Also in the School District DataFrame for the Thomas row, % passing math, % passing reading, and % overall passing all decreased after the analysis was redone.
