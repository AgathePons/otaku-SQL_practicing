# SQL requests - O'taku

## 1 - échantillonage

```sql
SELECT * FROM viewing ORDER BY random();
```
```sql
SELECT * FROM viewing ORDER BY random() LIMIT 15;
```

## 2- mode agrégé

**Exemple de fonction d'agrégat**

AVG() pour faire la moyenne (average).


```sql
SELECT AVG(viewer_age_group) from viewing;
```

**Exercice**

```sql
SELECT viewer_country, AVG(viewer_age_group) FROM viewing 
GROUP BY viewer_country 
ORDER BY AVG(viewer_age_group) DESC;
```

```sql
SELECT viewer_age_group, COUNT(*) FROM viewing 
GROUP BY viewer_age_group 
ORDER BY viewer_age_group DESC;
```

## 3- extract

**Extraire l'année de la date**

```sql
SELECT id, EXTRACT(YEAR FROM viewing_date) FROM viewing;
```

**Super bonus**

```sql
SELECT EXTRACT(YEAR FROM viewing_date), COUNT(*) 
FROM viewing 
GROUP BY EXTRACT(YEAR FROM viewing_date);
```