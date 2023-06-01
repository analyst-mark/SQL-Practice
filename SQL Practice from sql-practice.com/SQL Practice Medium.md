
**1. Show unique birth years from patients and order them by ascending.**

![](src-img/Pasted%20image%2020230524132611.png)

![](src-img/Pasted%20image%2020230524132616.png)

2. Show unique first names from the patients table which only occurs once in the list.  
For example, if two or more people are named 'John' in the first_name column then don't include their name in the output list. If only 1 person is named 'Leo' then include them in the output. 


![](src-img/Pasted%20image%2020230524132742.png)

![](src-img/Pasted%20image%2020230524132748.png)

3. Show patient_id and first_name from patients where their first_name start and ends with 's' and is at least 6 characters long.

![](src-img/Pasted%20image%2020230524132845.png)

![](src-img/Pasted%20image%2020230524132838.png)

4. Show patient_id, first_name, last_name from patients whose diagnosis is 'Dementia'.  
  Primary diagnosis is stored in the admissions table.

![](src-img/Pasted%20image%2020230524133030.png)

![](src-img/Pasted%20image%2020230524133038.png)

5. Display every patient's first_name.  
Order the list by the length of each name and then by alphbetically

![](src-img/Pasted%20image%2020230524133357.png)

![](src-img/Pasted%20image%2020230524133414.png)

6. Show the total amount of male patients and the total amount of female patients in the patients table.   Display the two results in the same row.

![](src-img/Pasted%20image%2020230524133855.png)

![](src-img/Pasted%20image%2020230524133911.png)

7.  Show first and last name, allergies from patients which have allergies to either 'Penicillin' or 'Morphine'. Show results ordered ascending by allergies then by first_name then by last_name.

![](src-img/Pasted%20image%2020230524134505.png)


![](src-img/Pasted%20image%2020230524134511.png)

8.  Show patient_id, diagnosis from admissions. Find patients admitted multiple times for the same diagnosis.

![](src-img/Pasted%20image%2020230524134719.png) 

![](src-img/Pasted%20image%2020230524134747.png)

9. Show the city and the total number of patients in the city.  
Order from most to least patients and then by city name ascending.

![](src-img/Pasted%20image%2020230524134940.png)

![](src-img/Pasted%20image%2020230524134946.png)

10. Show first name, last name and role of every person that is either patient or doctor.  
The roles are either "Patient" or "Doctor"

![](src-img/Pasted%20image%2020230524135030.png)

![](src-img/Pasted%20image%2020230524135037.png)

11. Show all allergies ordered by popularity. Remove 'NKA' and NULL values from query.

![](src-img/Pasted%20image%2020230524135402.png)

![](src-img/Pasted%20image%2020230524135409.png)

11. Show all patient's first_name, last_name, and birth_date who were born in the 1970s decade. Sort the list starting from the earliest birth_date.

![](src-img/Pasted%20image%2020230524135451.png)

![](src-img/Pasted%20image%2020230524135459.png)

12. We want to display each patient's full name in a single column. Their last_name in all upper letters must appear first, then first_name in all lower case letters. Separate the last_name and first_name with a comma. Order the list by the first_name in decending order  
	EX:  SMITH,jane

![](src-img/Pasted%20image%2020230524135610.png)

![](src-img/Pasted%20image%2020230524135619.png)


13.  Show the province_id(s), sum of height; where the total sum of its patient's height is greater than or equal to 7,000.

![](src-img/Pasted%20image%2020230524135700.png)

![](src-img/Pasted%20image%2020230524135708.png)

14. Show the difference between the largest weight and smallest weight for patients with the last name 'Maroni'

![](src-img/Pasted%20image%2020230524135833.png)

![](src-img/Pasted%20image%2020230524135841.png)

15. Show all of the days of the month (1-31) and how many admission_dates occurred on that day. Sort by the day with most admissions to least admissions.

![](src-img/Pasted%20image%2020230524135928.png)

![](src-img/Pasted%20image%2020230524135938.png)

16.  Show the all columns for patient_id 542's most recent admission_date.

![](src-img/Pasted%20image%2020230524140521.png)

OR

![](src-img/Pasted%20image%2020230524140248.png)

![](src-img/Pasted%20image%2020230524140255.png)

17.  Show patient_id, attending_doctor_id, and diagnosis for admissions that match one of the two criteria:  
	1. patient_id is an odd number and attending_doctor_id is either 1, 5, or 19.  
	2. attending_doctor_id contains a 2 and the length of patient_id is 3 characters.

![](src-img/Pasted%20image%2020230524141025.png)

![](src-img/Pasted%20image%2020230524141033.png)

18.  Show first_name, last_name, and the total number of admissions attended for each doctor.  
		Every admission has been attended by a doctor.

![](src-img/Pasted%20image%2020230524141115.png)

![](src-img/Pasted%20image%2020230524141150.png)

19. For each doctor, display their id, full name, and the first and last admission date they attended.

![](src-img/Pasted%20image%2020230524141540.png)

![](src-img/Pasted%20image%2020230524141548.png)

20. Display the total amount of patients for each province. Order by descending.

![](src-img/Pasted%20image%2020230524141726.png)


shorter version 
![](src-img/Pasted%20image%2020230524141856.png)


![](src-img/Pasted%20image%2020230524141736.png)

21. For every admission, display the patient's full name, their admission diagnosis, and their doctor's full name who diagnosed their problem.

![](src-img/Pasted%20image%2020230524142338.png)

![](src-img/Pasted%20image%2020230524142345.png)


22. Display the number of duplicate patients based on their first_name and last_name.

![](src-img/Pasted%20image%2020230524142902.png)

![](src-img/Pasted%20image%2020230524142909.png)

23. Display patient's full name, height in the unit feet rounded to 1 decimal,  weight in the unit pounds rounded to 0 decimals, birth_date,  gender non abbreviated.  
		Convert CM to feet by dividing by 30.48.  
		Convert KG to pounds by multiplying by 2.205.

![](src-img/Pasted%20image%2020230524231115.png)


![](src-img/Pasted%20image%2020230524231123.png)