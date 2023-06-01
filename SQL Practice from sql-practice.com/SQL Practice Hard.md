1. Show all of the patients grouped into weight groups.  
	Show the total amount of patients in each weight group.  
	Order the list by the weight group decending.  
	For example, if they weight 100 to 109 they are placed in the 100 weight group, 110-119 = 110 weight group, etc.

![](src-img/Pasted%20image%2020230524232648.png)

![](src-img/Pasted%20image%2020230524232654.png)

2.  Show patient_id, weight, height, isObese from the patients table.  
	  Display isObese as a boolean 0 or 1.  
	  Obese is defined as weight(kg)/(height(m)2) >= 30.  
	  weight is in units kg.  
	  height is in units cm.

![](src-img/Pasted%20image%2020230524234542.png)

![](src-img/Pasted%20image%2020230524234548.png)


3. Show patient_id, first_name, last_name, and attending doctor's specialty.  
Show only the patients who has a diagnosis as 'Epilepsy' and the doctor's first name is 'Lisa'  
  
Check patients, admissions, and doctors tables for required information.

![](src-img/Pasted%20image%2020230524235201.png)

![](src-img/Pasted%20image%2020230524235206.png)

4. All patients who have gone through admissions, can see their medical documents on our site. Those patients are given a temporary password after their first admission. Show the patient_id and temp_password.  
  
	The password must be the following, in order:  
	1. patient_id  
	2. the numerical length of patient's last_name  
	3. year of patient's birth_date

![](src-img/Pasted%20image%2020230525103721.png)

![](src-img/Pasted%20image%2020230525103729.png)

5. Each admission costs $50 for patients without insurance, and $10 for patients with insurance. All patients with an even patient_id have insurance.  
  
	Give each patient a 'Yes' if they have insurance, and a 'No' if they don't have insurance. Add up the admission_total cost for each has_insurance group.

![](src-img/Pasted%20image%2020230525105258.png)

![](src-img/Pasted%20image%2020230525105304.png)

alternative solution

![](src-img/Pasted%20image%2020230525105336.png)

From statement -- create a subquery , then select the records in it to create the final solution

![](src-img/Pasted%20image%2020230525105431.png)


![](src-img/Pasted%20image%2020230525105422.png)

![](src-img/Pasted%20image%2020230525105457.png)

6. Show the provinces that has more patients identified as 'M' than 'F'. Must only show full province_name

![](src-img/Pasted%20image%2020230525115919.png)

![](src-img/Pasted%20image%2020230525115932.png)

7. We are looking for a specific patient. Pull all columns for the patient who matches the following criteria:  
	- First_name contains an 'r' after the first two letters.  
	- Identifies their gender as 'F'  
	- Born in February, May, or December  
	- Their weight would be between 60kg and 80kg  
	- Their patient_id is an odd number  
	- They are from the city 'Kingston'

![](src-img/Pasted%20image%2020230525121208.png)


![](src-img/Pasted%20image%2020230525121214.png)

8. Show the percent of patients that have 'M' as their gender. Round the answer to the nearest hundreth number and in percent form.

![](src-img/Pasted%20image%2020230525123617.png)

![](src-img/Pasted%20image%2020230525123624.png)

alternative answer using AVG 

![](src-img/Pasted%20image%2020230525123716.png)

![](src-img/Pasted%20image%2020230525123624%201.png)

9. For each day display the total amount of admissions on that day. Display the amount changed from the previous date.

![](src-img/Pasted%20image%2020230525124549.png)

![](src-img/Pasted%20image%2020230525124602.png)

10. Sort the province names in ascending order in such a way that the province 'Ontario' is always on top.

![](src-img/Pasted%20image%2020230525125312.png)

![](src-img/Pasted%20image%2020230525125319.png)







