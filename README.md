# Guide des Commandes PostgreSQL

Ce document est un guide pratique pour apprendre à utiliser PostgreSQL via le terminal. Il couvre les commandes de base pour la gestion des bases de données, des utilisateurs, et des tables. Chaque commande est accompagnée d'exemples pour faciliter la compréhension.

---

## **1. Installation de PostgreSQL**

### Sur macOS avec Homebrew
1. Vérifiez si Homebrew est installé :
   ```bash
   brew --version
   ```
2. Si Homebrew n'est pas installé :
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
3. Installez PostgreSQL :
   ```bash
   brew install postgresql
   ```
4. Démarrez PostgreSQL :
   ```bash
   brew services start postgresql
   ```
5. Vérifiez l'installation :
   ```bash
   psql --version
   ```

---

## **2. Lancer PostgreSQL**

Connectez-vous à PostgreSQL depuis le terminal :
```bash
psql postgres
```

Si vous souhaitez vous connecter à une base spécifique ou avec un utilisateur particulier :
```bash
psql -U <nom_utilisateur> -d <nom_base>
```

### Quitter PostgreSQL
```bash
\q
```

---

## **3. Commandes de Base PostgreSQL**

### **Gestion des Bases de Données**

- **Lister les bases de données :**
  ```sql
  \l
  ```

- **Créer une base de données :**
  ```sql
  CREATE DATABASE ma_base;
  ```
  Exemple :
  ```sql
  CREATE DATABASE boutique;
  ```

- **Se connecter à une base de données :**
  ```sql
  \c ma_base
  ```

- **Supprimer une base de données :**
  ```sql
  DROP DATABASE ma_base;
  ```

---

### **Gestion des Utilisateurs**

- **Créer un utilisateur :**
  ```sql
  CREATE USER paul WITH PASSWORD 'mon_mot_de_passe';
  ```

- **Modifier le mot de passe d'un utilisateur :**
  ```sql
  ALTER USER paul WITH PASSWORD 'nouveau_mot_de_passe';
  ```

- **Donner des droits à un utilisateur sur une base :**
  ```sql
  GRANT ALL PRIVILEGES ON DATABASE ma_base TO paul;
  ```

- **Supprimer un utilisateur :**
  ```sql
  DROP USER paul;
  ```

---

### **Gestion des Tables**

#### Créer une table
```sql
CREATE TABLE nom_table (
    colonne1 TYPE_DE_DONNEE,
    colonne2 TYPE_DE_DONNEE,
    ...
);
```
Exemple :
```sql
CREATE TABLE produits (
    id SERIAL PRIMARY KEY,
    nom VARCHAR(100),
    prix DECIMAL(10, 2),
    date_creation TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### Afficher les tables existantes
```sql
\dt
```

#### Insérer des données
```sql
INSERT INTO nom_table (colonne1, colonne2) VALUES ('valeur1', 'valeur2');
```
Exemple :
```sql
INSERT INTO produits (nom, prix) VALUES ('Ordinateur', 999.99);
INSERT INTO produits (nom, prix) VALUES ('Souris', 19.99);
```

#### Lire les données d'une table
```sql
SELECT * FROM nom_table;
```
Exemple :
```sql
SELECT * FROM produits;
```

#### Mettre à jour une donnée
```sql
UPDATE nom_table SET colonne = 'nouvelle_valeur' WHERE condition;
```
Exemple :
```sql
UPDATE produits SET prix = 899.99 WHERE nom = 'Ordinateur';
```

#### Supprimer une donnée
```sql
DELETE FROM nom_table WHERE condition;
```
Exemple :
```sql
DELETE FROM produits WHERE nom = 'Souris';
```

#### Supprimer une table
```sql
DROP TABLE nom_table;
```
Exemple :
```sql
DROP TABLE produits;
```

---

### **Commandes Utiles**

- **Afficher la structure d'une table :**
  ```sql
  \d nom_table
  ```

- **Lister les schémas :**
  ```sql
  \dn
  ```

- **Changer le schéma par défaut :**
  ```sql
  SET search_path TO nom_schema;
  ```

---

## **4. Exercices Pratiques**

### **Exercice 1 : Gestion de la base de données**
1. Créez une base de données appelée `test_db`.
2. Connectez-vous à cette base.
3. Créez une table `utilisateurs` avec les colonnes `id`, `nom`, `email`, et `date_inscription`.
4. Insérez trois utilisateurs dans cette table.
5. Affichez tous les utilisateurs.
6. Modifiez l'email d'un utilisateur.
7. Supprimez un utilisateur.
8. Supprimez la table et la base de données.

### **Exercice 2 : Gestion des utilisateurs**
1. Créez un utilisateur `dev_user` avec le mot de passe `secure_pass`.
2. Donnez-lui les droits sur une base appelée `dev_db`.
3. Changez son mot de passe.
4. Supprimez cet utilisateur.

---

## **5. Ressources Supplémentaires**

- [Documentation officielle PostgreSQL](https://www.postgresql.org/docs/)
- [Tutoriels PostgreSQL](https://www.postgresqltutorial.com/)
