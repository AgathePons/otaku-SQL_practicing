# SQL AGGREGATIONS

**GROUP BY**

```sql
SELECT viewer_country, COUNT(viewer_country) FROM viewing GROUP BY viewer_country ORDER BY count DESC;
```

**Moyenne**

```sql
SELECT viewer_country, avg(viewer_age_group) FROM viewing GROUP BY viewer_country;
```

**Min / Max**

```sql
SELECT viewer_country, min(viewer_age_group) FROM viewing GROUP BY viewer_country;
```

```sql
SELECT viewer_country, max(viewer_age_group) FROM viewing GROUP BY viewer_country;
```

```sql
SELECT show_name, max(season) FROM viewing GROUP BY show_name;
```

```sql
SELECT season, max(episode) FROM viewing WHERE show_name='Sherclock' GROUP BY season ORDER BY season;
```

**Having**

```sql
SELECT viewer_country, COUNT(*) FROM viewing GROUP BY viewer_country HAVING count(*) > 10000;
```