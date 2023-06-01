```sql
select first_name,last_name, count(*),
		case 
        	when required_date > shipped_date then "On Time"
            	else "Late"
            end as shipped
from employees e 
join orders o 
	on e.employee_id = o.employee_id
group by 1,2,4
order by 2,1,3 desc
```