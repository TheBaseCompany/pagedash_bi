# Users
```sql users
select * from pagedash.users
```

<DataTable data={users} />

Summary of users in the database.

# Total users
```sql user_count
select count(*) as user_count from pagedash.users
```
We have a total of <Value data={user_count} /> users in the database.
User by week
```sql users_by_day
select 
    date_trunc('day', created_at) as day,
    count(*) as user_count
from pagedash.users
group by day 
```
Draw a line chart of users by day.
<LineChart
    data={users_by_day}
    title="Users by Week"
    x=day
    y=user_count
/>