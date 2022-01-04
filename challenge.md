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

**Correction:** On pouvait faire un peu plus simple et mieux.

```sql
SELECT EXTRACT(YEAR FROM viewing_date) AS date, COUNT(*) AS visionnage
FROM viewing 
GROUP BY date 
ORDER BY date DESC;
```

## Little bonus from correction

**Offset**

Permet de décaler de xx les résultats (au lieu) d'avoir les 15 premiers résultats, on aura ici les résultats du 16e au 30e.

```sql
SELECT * FROM viewing OFFSET 15 LIMIT 15;
```

On s'en sert pour créer des paginations en mettant un `offset` de même valeur qu'une `limit`. Ensuite on multiplie l'`offset` de base pour décaler d'un nouveau cran à chaque nouvelle page.

```sql
SELECT * FROM viewing OFFSET (15*2) LIMIT 15;
```
*Ici page 3*

**AS pour renommer un champ**

On peut utiliser AS pour renommer une colonne :

```sql
SELECT viewer_age_group AS age, COUNT(*) AS views FROM viewing 
GROUP BY viewer_age_group 
ORDER BY viewer_age_group DESC;
```