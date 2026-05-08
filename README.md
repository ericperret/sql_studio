# SQL Studio

**Un interpréteur SQL complet qui tourne dans votre navigateur — zéro serveur, zéro dépendance, un seul fichier HTML.**

---

## Origine

La base de données embarquée est une mini base de support pédagogique librement copiée depuis l'image d'un quiz DGSE. Trois tables, des jointures naturelles, des NULLs intentionnels — tout ce qu'il faut pour apprendre SQL sans friction.

---

## Ce que c'est

Un outil pédagogique pour apprendre et pratiquer SQL, entièrement autonome. Pas de Node.js. Pas de Python. Pas de CDN. Pas de framework. Ouvrez le fichier dans Firefox ou Chrome — c'est prêt.

---

## Le moteur SQL

C'est la pièce maîtresse. Un interpréteur SQL écrit en JavaScript pur (~400 lignes) capable d'exécuter de vraies requêtes sur de vraies données en mémoire.

**Requêtes supportées :**

- `SELECT` avec colonnes nommées, alias `AS`, `*`
- `SELECT DISTINCT`
- `FROM` avec alias de table
- `INNER JOIN` et `LEFT JOIN` (avec `ON` et gestion des NULLs)
- Jointures multiples (3 tables ou plus)
- `WHERE` avec `AND`, `OR`, `IN`, `NOT IN`, `IS NULL`, `IS NOT NULL`, opérateurs `=` `!=` `>` `<` `>=` `<=`
- `CASE WHEN ... THEN ... ELSE ... END` avec calcul arithmétique (`+`)
- `ORDER BY` multi-colonnes `ASC` / `DESC`
- `SELECT DISTINCT`
- `LIMIT`

**DDL/DML supportés :**

- `CREATE TABLE`
- `DROP TABLE`
- `INSERT INTO ... VALUES`
- `UPDATE ... SET ... WHERE`
- `DELETE FROM ... WHERE`

**Ce que le moteur fait bien :**

Les NULLs sont traités correctement. Un `LEFT JOIN` sur une clé étrangère NULL conserve la ligne avec des colonnes droites à NULL — exactement comme un vrai SGBD. Le scoring `CASE WHEN` additionne proprement plusieurs expressions. Les alias de tables sont résolus dans les conditions `ON` et `WHERE` sans ambiguïté.

---

## L'interface

```
┌─ TABLES ──────────┬─ MOTS-CLÉS ─────────────────────────────────────┐
│                   │ SELECT  DISTINCT  FROM  WHERE  ORDER BY  ASC ... │
│ ▶ base      4 lg  ├─ QUESTION ──────────────────────────────────────┤
│ ▶ officer   5 lg  │ 💡  Niveau 5 — INNER JOIN · 6/15    ● ● ○ ○    │
│ ▶ missions  5 lg  │ Affichez le nom de chaque mission avec le nom... │
│                   ├─ ÉDITEUR SQL ───────────────────────────────────┤
│                   │ SELECT m.name, b.name                           │
│                   │ FROM missions m                                 │
│                   │ INNER JOIN base b ON m.base_id = b.id           │
│                   │                                                 │
│                   │ [ ▶ EXÉCUTER ]  [ ↺ ]          Ctrl+Enter      │
│                   ├─ RÉSULTATS ─────────────────────────────────────┤
│                   │ ✔ CORRECT                                       │
│                   │ Référence : SELECT m.name, b.name FROM ...      │
│                   │                                                 │
│                   │ name          | name                            │
│                   │ design_plans  | Scaraf                          │
│                   │ ...                                             │
└───────────────────┴─────────────────────────────────────────────────┘
```

---

## Le mode Training

15 exercices progressifs sur 10 niveaux :

| Niveau | Thème | Questions |
|--------|-------|-----------|
| 1 | SELECT | 1 |
| 2 | WHERE | 1 |
| 3 | AND / OR / IS NULL | 1 |
| 4 | DISTINCT · ORDER BY | 2 |
| 5 | INNER JOIN | 2 |
| 6 | LEFT JOIN | 2 |
| 7 | 3 tables | 2 |
| 8 | CASE WHEN | 2 |
| 9 | INSERT | 1 |
| 10 | CREATE TABLE | 1 |

**La validation porte sur le résultat, pas sur la syntaxe.** Deux requêtes différentes qui produisent le même output sont toutes les deux acceptées.

Niveaux 4 à 8 : après 5 erreurs → indice. Après 10 erreurs → solution + question reformulée différemment.

La progression est sauvegardée en `localStorage` — elle survit au rechargement.

Chaque niveau dispose d'une bulle de cours académique (bouton 💡) avec exemples.

---

## Import / Export

- **⬇ démo** : charge la base DGSE (3 tables)
- **↑ CSV** : importe n'importe quel fichier `.csv` comme nouvelle table, types auto-détectés
- **↓ CSV** : exporte le résultat de la dernière requête SELECT
- **✕ reset** : efface tout

---

## Utilisation

```
Télécharger sql_studio.html → Ouvrir dans un navigateur → C'est tout.
```

Aucune installation. Aucun serveur. Fonctionne hors ligne.

---

## Licence

Libre de droits. Copiez, modifiez, redistribuez.
