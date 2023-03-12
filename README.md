# Chicago Schools Data Analysis
  *Objectives
  ___________________________________________________________________________________________
  * Understand the dataset for Chicago Public School level performance
  * Store the dataset in an Db2 database on IBM Cloud instance
  * Retrieve metadata about tables and columns and query data from mixed case columns
  * Solve example problems to practice your SQL skills including using built-in database functions
 ___________________________________________________________________________________________________
 * Data set: https://data.cityofchicago.org/Education/Chicago-Public-Schools-Progress-Report-Cards-2011-/9xs2-f89t?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork22-2022-01-01&cm_mmc=Email_Newsletter-_-Developer_Ed%2BTech-_-WW_WW-_-SkillsNetwork-Courses-IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork-20127838&cm_mmca1=000026UJ&cm_mmca2=10006555&cm_mmca3=M12345678&cvosrc=email.Newsletter.M12345678&cvo_campaign=000026UJ
 
 * also available as an attached csv file named: ChicagoPublicSchools.csv
 * FinalAssignmentNoteBookOFChicagoSchoolsAsHTMLImage is an image of the project
 * tableSchoolColumnNames.txt has the names of the columns of the SCHOOLS Table

 __________________________________________________________________________________________________________
 
 * Steps Taken to accomplish this project
 __________________________________________________________________________________________________________
 * 1- Downloaded ChicagoPublicSchools.csv
 * 2- Loaded data into IBM database DB2
 * 3- Connected to database with python jupiter notbook
 * 4- Used (%sql select distinct(name), coltype, length from sysibm.syscolumns where tbname= 'SCHOOLS') to check connection success and retreive the table columns scheme
 * 5- Used (%sql select count(*) from SYSCAT.COLUMNS where TABNAME = 'SCHOOLS') to retrieve the number of columns in table SCHOOLS
 * 6- Used (%sql select count(*) from SCHOOLS where ELEMENTARY__MIDDLE__OR_HIGH_SCHOOL = 'ES';) to return the number of Elementary schools in table SCHOOLS
 * 7- Used (%sql select max(SAFETY_SCORE) from SCHOOLS;) to return the heighest saftey score in table SCHOOLS
 * 8- Used (%sql select Name_of_School, Safety_Score from SCHOOLS where Safety_Score= (select MAX(Safety_Score) from SCHOOLS)) to return the schools have the heighest score in table SCHOOLS
 * 9- Used (%sql select Name_of_School, AVERAGE_STUDENT_ATTENDANCE from SCHOOLS where average_student_attendance != 'None' Order BY AVERAGE_STUDENT_ATTENDANCE desc LIMIt 10;) to retreive the top 10 schools with the highest "Average Student Attendance
 * 10- Used (%sql select Name_of_School, AVERAGE_STUDENT_ATTENDANCE from SCHOOLS where average_student_attendance != 'None' Order BY AVERAGE_STUDENT_ATTENDANCE asc LIMIt 5;) to retreive a list of 5 Schools with the lowest Average Student Attendance
 * 11- Used (%sql select Name_of_School, replace(AVERAGE_STUDENT_ATTENDANCE, '%', '') from SCHOOLS where average_student_attendance != 'None' Order BY AVERAGE_STUDENT_ATTENDANCE asc LIMIt 5;) to replace the % with ''
 * 12- Used (%sql select Name_of_School, AVERAGE_STUDENT_ATTENDANCE from SCHOOLS where DECIMAL(replace(AVERAGE_STUDENT_ATTENDANCE, '%', '')) < 70;) to retrieve the schools that has average student attendance < 70%
 * 13- Used (%sql select COMMUNITY_AREA_NAME, sum(College_Enrollment) As "Total Enrollment" from SCHOOLS group by  COMMUNITY_AREA_NAME) to get the total College Enrollment for each Community Area 
 * 14- Used (%sql select COMMUNITY_AREA_NAME, sum(College_Enrollment) As "Total Enrollment" from SCHOOLS group by  COMMUNITY_AREA_NAME order by "Total Enrollment" asc limit 5) To Get the 5 Community Areas with the least total College Enrollment sorted in ascending order
 * 15- Used (%sql select Name_of_School, safety_score from SCHOOLS Order BY safety_score asc LIMIt 5;) to get a list of 5 schools with lowest safety score
 * 16- Used (%sql select hardship_index from chicago_socioeconomic_data CD, schools CPS \
where CD.ca = CPS.community_area_number \
     and college_enrollment = 4368) to get the hardship index for the community area which has College Enrollment of 4368
     NOTE(table chicago_socioeconomic_data was used here)
 * 17- Used (%sql select ca, community_area_name, hardship_index from chicago_socioeconomic_data \
  where ca in \
  ( select community_area_number from schools order by college_enrollment desc limit 1 )) to Get the hardship index for the community area which has the school with the highest enrollment

  _______________________________________________________________________________________________________________________________________________________
  
