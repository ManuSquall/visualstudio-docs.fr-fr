---
title: "Intégration de SQL Server avec les Outils R pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 919dfc34-234a-489e-91bf-74a4cefae26c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 44ae1fd825997ff5eab1448ebd86f88a130172a1
ms.contentlocale: fr-fr
ms.lasthandoff: 05/12/2017

---


# <a name="working-with-sql-server-and-r"></a>Utilisation de SQL Server et R

Les Outils R pour Visual Studio (RTVS) tirent parti de l’excellente prise en charge de SQL Server par Visual Studio pour simplifier l’utilisation des bases de données SQL par les scientifiques des données, notamment en ce qui concerne la création et l’exécution de requêtes SQL et l’utilisation de procédures stockées.

> [!Note]
> Pour utiliser conjointement SQL et R, vous devez installer SQL Server Data Tools :
> - Visual Studio 2017 : exécutez le programme d’installation de Visual Studio et sélectionnez la charge de travail Stockage et traitement des données, qui comprend SQL Server Data Tools.
> - Visual Studio 2015 : suivez les instructions fournies dans [Download SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).

La vidéo suivante (3m 03s) fournit une brève présentation de SQL Server et R :

<iframe width="560" height="315" src="https://www.youtube.com/embed/n4AYr0QIwdQ" frameborder="0" allowfullscreen></iframe>

## <a name="creating-and-running-sql-queries"></a>Création et exécution de requêtes SQL

RTVS prend en charge l’ajout de requêtes SQL à des projets R, ce qui vous permet de développer des requêtes SQL itérativement dans un contexte distinct jusqu’à obtenir les résultats souhaités.

Pour ajouter un fichier de requête SQL, cliquez sur le projet dans l’Explorateur de solutions, sélectionnez **Ajouter > Nouvel élément**, puis sélectionnez le type de fichier **Requête SQL** :

![Ajouter un élément de requête SQL à un projet](~/docs/rtvs/media/sql-add-item.png)

Le fichier s’ouvre dans l’éditeur Transact-SQL de Visual Studio, qui fournit des fonctionnalités IntelliSense complètes pour SQL et la possibilité d’exécuter des requêtes. Pour utiliser ces fonctionnalités, cependant, vous devez vous connecter à une base de données à l’aide du bouton de connexion situé dans la barre d’outils de l’éditeur ou simplement essayer d’exécuter une requête (Ctrl+Maj+E, qui fonctionne également sur une sélection). Dans les deux cas, la boîte de dialogue de connexion apparaît :

![Boîte de dialogue de connexion SQL](~/docs/rtvs/media/sql-connection-dialog.png)

Une fois qu’une connexion est établie, vous pouvez exécuter des requêtes et afficher les résultats :

![Résultats de requête SQL](~/docs/rtvs/media/sql-query-results.png)

L’éditeur Transact-SQL prend en charge de nombreuses autres fonctionnalités, telles que l’affichage du plan d’exécution de la requête et un débogueur de requête. Pour plus d’informations, consultez [Utiliser l’Éditeur Transact-SQL pour modifier et exécuter des scripts](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="working-with-sql-server-stored-procedures"></a>Utilisation de procédures stockées SQL Server

[SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 et versions ultérieures) vous permet d’incorporer et d’exécuter du code R à partir d’une procédure stockée T-SQL. Cela signifie que vous pouvez exécuter du code R sur un ordinateur SQL Server, traiter les données retournées par une requête SQL, et générer un jeu de résultats SQL qui peut être traité par du code SQL supplémentaire ou retourné au client.

RTVS simplifie le processus de combinaison du code R et SQL (processus plutôt complexe et sujet aux erreurs) à l’intérieur d’une instruction SQL unique, comme décrit dans les sections suivantes :

- [Ajouter une connexion de base de données](#add-a-database-connection)
- [Écrire et tester une procédure stockée SQL](#write-and-test-a-sql-stored-procedure)
- [Publier une procédure stockée SQL](#publish-a-sql-stored-procedure)

La vidéo suivante (6m 09s) fournit également une vue d’ensemble de ces fonctionnalités :

<iframe width="560" height="315" src="https://www.youtube.com/embed/dFKIT2OitWQ" frameborder="0" allowfullscreen></iframe>

### <a name="add-a-database-connection"></a>Ajouter une connexion de base de données

1. Sélectionnez **Outils R > Données > Ajouter une connexion de base de données** pour afficher la boîte de dialogue **Propriétés de connexion**, dans laquelle vous spécifiez le nom de la source de données (SQL Server dans le cas présent), le nom du serveur, le mode d’authentification et le nom de la base de données. Vous pouvez sélectionner **Tester la connexion** pour vérifier votre entrée avant de fermer la boîte de dialogue.
 
    ![Boîte de dialogue de connexion SQL](~/docs/rtvs/media/sql-connection-string-dialog.png)

1. Une fois que vous avez sélectionné **OK** avec une connexion valide, Visual Studio génère une chaîne de connexion nommée `dbConnection` dans un nouveau fichier `settings.R`. RTVS exécute automatiquement ce fichier. Vous pouvez donc utiliser immédiatement la connexion à partir de scripts R :

![Fichier Settings.R SQL](~/docs/rtvs/media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Écrire et tester une procédure stockée SQL

Pour ajouter une nouvelle procédure stockée SQL, cliquez sur votre projet, sélectionnez **Ajouter > Nouvel élément**, sélectionnez **Procédure stockée SQL avec R** dans la liste des modèles, nommez le fichier (`StoredProcedure.R` dans cet exemple), puis sélectionnez **OK**.
 
RTVS crée trois fichiers pour la procédure stockée : un fichier `.R` pour votre code R, un fichier `.Query.sql` pour le code SQL et un fichier `.Template.sql` qui combine les deux. Ces deux derniers fichiers apparaissent dans l’Explorateur de solutions en tant qu’enfants du fichier `.R` :

![Affichage développé de la procédure stockée SQL avec R dans l’Explorateur de solutions](~/docs/rtvs/media/sql-solution-explorer-expanded.png)

`StoredProcedure.R` (dans cet exemple) est l’emplacement où vous écrirez votre code R. Le contenu par défaut est le suivant :

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

En gros, le code reçoit une tramedonnées R nommée `InputDataSet` et retourne son résultat dans `OutputDataSet`, le code du modèle ne faisant que copier l’entrée dans la sortie.

> [!Note]
> Les noms de ces tramedonnées sont contrôlés par les paramètres `@input_data_1_name` et `@output_data_1_name` dans l’appel à la procédure stockée système `sp_execute_external_script`. Pour plus d’informations sur la conception de cette convention d’appel et pour obtenir des exemples de son utilisation, consultez [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

L’autre code généré dans les commentaires est un petit script de test qui utilise le [package RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) pour transmettre une instruction SQL à SQL Server, l’exécuter, puis récupérer son jeu de résultats sous forme de tramedonnées R. Vous pouvez supprimer les marques de commentaire de ce code de test pour écrire votre code R de manière interactive par rapport au jeu de résultats que vous obtenez à partir de SQL Server.

`StoredProcedure.Query.sql` est l’emplacement où vous écrivez et testez la requête SQL qui génère les données pour `InputDataSet`. S’agissant d’un fichier `.sql`, vous bénéficiez de toutes les fonctionnalités de l’éditeur Transact-SQL à votre disposition.

Une fois que vous êtes satisfait de votre code SQL, vous pouvez facilement l’intégrer à votre code R dans `StoredProcedure.R` en faisant simplement glisser le fichier `.sql` sur l’éditeur ouvert pour le fichier `.R`. Dans l’image ci-dessous, `StoredProcedure.Query.sql` a été déplacé vers le point après la virgule dans `sqlQuery(channel, )` :

![Lecture de fichier SQL dans une variable de chaîne R](~/docs/rtvs/media/sql-reference-sql-file-from-r.png)

Comme vous pouvez le voir, cette étape génère automatiquement le code R pour ouvrir le fichier `.sql`, lire son contenu dans une chaîne et le passer au package RODBC pour l’envoyer à SQL Server.

Tout ceci étant en place, vous pouvez maintenant écrire de manière interactive du code R qui manipule la tramedonnées `InputDataSet` comme vous le souhaitez. N’oubliez pas que vous pouvez simplement sélectionner le code R dans l’éditeur et l’envoyer à la [Fenêtre interactive](interactive-repl.md) en appuyant sur Ctrl+Entrée.

`StoredProcedure.Template.sql`, pour finir, contient le modèle pour la génération de votre procédure stockée SQL :

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- L’espace réservé `_RCODE_` est remplacé par le contenu de `StoredProcedure.R`.
- L’espace réservé `_INPUT_QUERY_` est remplacé par le contenu de `StoredProcedure.Query.sql`.
- Vous devez décrire le schéma du jeu de résultats retourné par la procédure stockée en modifiant la clause `WITH RESULT SETS`. Identifiez spécifiquement les colonnes de la tramedonnées `OutputDataSet` que vous souhaitez retourner à l’appelant de la procédure stockée. 

Par exemple, pour la requête suivante :

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Vous devez utiliser la clause `WITH RESULT SETS` suivante pour spécifier les types de données des valeurs de retour :

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publier une procédure stockée SQL

1. Sélectionnez la commande de menu **Outils R > Données > Publier avec des options**.
1. Dans la boîte de dialogue qui s’affiche, remplacez **Publier sur** par **Base de données**, spécifiez la cible, sélectionnez **Publier**, et RTVS crée et publie la procédure stockée :

    ![Boîte de dialogue de publication de procédure stockée](~/docs/rtvs/media/sql-publish-with-options.png)

1. Pour publier toutes les procédures stockées dans un projet, vous pouvez également utiliser la commande **Outils R > Données > Publier les procédures stockées**, qui est également disponible quand vous cliquez avez le bouton droit sur le projet dans l’Explorateur de solutions.

> [!Tip]
> Si l’Explorateur d’objets SQL Server est ouvert dans Visual Studio, vous verrez également votre procédure stockée publiée dans le dossier **Programmabilité > Procédures stockées** de votre base de données. Vous pouvez aussi l’exécuter à partir de l’Explorateur d’objets en cliquant avec le bouton droit et en sélectionnant **Exécuter la procédure**, ou en l’appelant de façon interactive à partir d’une fenêtre de requête `.sql`.

