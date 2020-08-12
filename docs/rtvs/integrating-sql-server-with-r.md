---
title: Intégration de SQL Server avec R
description: Visual Studio prend en charge la création et l’exécution de requêtes SQL à partir de R, et permet d’utiliser R avec des procédures stockées.
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 2b239059f445d92a5be6709ee7b7a26cb8bb7164
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144712"
---
# <a name="work-with-sql-server-and-r"></a>Utiliser SQL Server et R

L’excellente prise en charge de SQL Server par Visual Studio aide les scientifiques des données à utiliser les bases de données SQL et R avec la possibilité de créer et d’exécuter des requêtes SQL, et d’utiliser des procédures stockées.

> [!Note]
> Pour utiliser conjointement SQL et R, vous devez installer SQL Server Data Tools :
> - Visual Studio 2017 : exécutez le programme d’installation de Visual Studio et sélectionnez la charge de travail Stockage et traitement des données, qui comprend SQL Server Data Tools.
> - Visual Studio 2015 : suivez les instructions fournies dans [Download SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt).

:::row:::
    :::column:::
        ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo")
    :::column-end:::
    :::column:::
        [Regardez une vidéo (youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) qui offre une vue d’ensemble de SQL Server et de R (3 min 3 s).
    :::column-end:::
:::row-end:::

## <a name="create-and-run-sql-queries"></a>Créer et exécuter des requêtes SQL

RTVS prend en charge l’ajout de requêtes SQL à des projets R, ce qui vous permet de développer des requêtes SQL itérativement dans un contexte distinct jusqu’à obtenir les résultats souhaités.

Pour ajouter un fichier de requête SQL, cliquez avec le bouton droit sur le projet dans Explorateur de solutions, sélectionnez **Ajouter**un  >  **nouvel élément**, puis sélectionnez le type de fichier de **requête SQL** :

![Ajouter un élément de requête SQL à un projet](media/sql-add-item.png)

Cette commande ouvre le fichier dans l’Éditeur Transact-SQL de Visual Studio, qui fournit des fonctionnalités IntelliSense complètes pour SQL et la possibilité d’exécuter des requêtes. Pour que ces fonctionnalités fonctionnent, vous devez vous connecter à une base de données à l’aide du bouton de connexion dans la barre d’outils de l’éditeur ou essayer d’exécuter une requête (**CTRL** + **MAJ** + **E**, qui fonctionne également sur une sélection). Dans les deux cas, la boîte de dialogue de connexion apparaît :

![Boîte de dialogue de connexion SQL](media/sql-connection-dialog.png)

Une fois qu’une connexion est établie, vous pouvez exécuter des requêtes et afficher les résultats :

![Résultats de requête SQL](media/sql-query-results.png)

L’Éditeur Transact-SQL prend en charge de nombreuses autres fonctionnalités, telles que l’affichage du plan d’exécution de la requête et un débogueur de requête.
Pour plus d’informations, consultez [Utiliser l'Éditeur Transact-SQL pour modifier et exécuter des scripts](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="work-with-sql-server-stored-procedures"></a>Utiliser des procédures stockées SQL Server

[SQL Server R Services](/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 et versions ultérieures) vous permet d’incorporer et d’exécuter du code R à partir d’une procédure stockée T-SQL. Vous pouvez exécuter du code R sur un ordinateur SQL Server, traiter les données retournées par une requête SQL et générer un jeu de résultats SQL qui peut être traité par du code SQL supplémentaire ou retourné au client.

RTVS simplifie le processus de combinaison du code R et SQL (processus plutôt complexe et sujet aux erreurs) à l’intérieur d’une instruction SQL unique, comme décrit dans les sections suivantes :

- [Ajouter une connexion de base de données](#add-a-database-connection)
- [Écrire et tester une procédure stockée SQL](#write-and-test-a-sql-stored-procedure)
- [Publier une procédure stockée SQL](#publish-a-sql-stored-procedure)

:::row:::
    :::column:::
        ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo")
    :::column-end:::
    :::column:::
        [Regardez une vidéo (youtube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) qui offre une vue d’ensemble des procédures stockées de R et de SQL Server (6 min 9 s).
    :::column-end:::
:::row-end:::

### <a name="add-a-database-connection"></a>Ajouter une connexion de base de données

1. Sélectionnez **Outils R**  >  **données**  >  **Ajouter une connexion de base de données** pour afficher la boîte de dialogue **Propriétés de connexion** . Vous spécifiez ici le nom de la source de données (SQL Server dans le cas présent), le nom du serveur, le mode d’authentification et le nom de la base de données. Sélectionnez **Tester la connexion** pour vérifier votre entrée avant de fermer la boîte de dialogue.

    ![Boîte de dialogue de connexion SQL](media/sql-connection-string-dialog.png)

1. Une fois que vous avez sélectionné **OK** avec une connexion valide, Visual Studio génère une chaîne de connexion nommée `dbConnection` dans un nouveau fichier *settings.R*. RTVS exécute automatiquement ce fichier. Vous pouvez donc utiliser immédiatement la connexion à partir de scripts R :

![Fichier Settings.R SQL](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Écrire et tester une procédure stockée SQL

Pour ajouter une nouvelle procédure stockée SQL, cliquez avec le bouton droit sur votre projet, sélectionnez **Ajouter**un  >  **nouvel élément**, sélectionnez **procédure stockée SQL avec R** dans la liste des modèles, attribuez un nom au fichier, puis sélectionnez **OK**. Le nom de fichier par défaut est *SqlSProc.R* ; pour faciliter la lecture, le nom de fichier *StoredProcedure.R* est utilisé dans le reste de cette section. Si vous avez plusieurs procédures stockées, chaque fichier doit avoir un nom de fichier unique.

RTVS crée trois fichiers pour la procédure stockée : un fichier *.R* pour votre code R, un fichier *.Query.sql* pour le code SQL et un fichier *.Template.sql* qui combine les deux. Ces deux derniers fichiers apparaissent dans l’Explorateur de solutions en tant qu’enfants du fichier *.R* :

![Affichage développé de la procédure stockée SQL avec R dans l’Explorateur de solutions](media/sql-solution-explorer-expanded.png)

Le fichier *. R* (*StoredProcedure.R* cet exemple) est l’endroit où vous écrivez le code R. Le contenu par défaut est le suivant :

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
> Les noms de ces tramedonnées sont contrôlés par les paramètres `@input_data_1_name` et `@output_data_1_name` dans l’appel à la procédure stockée système `sp_execute_external_script`. Pour plus d’informations sur la conception de cette convention d’appel et pour obtenir des exemples de son utilisation, consultez [sp_execute_external_script (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

L’autre code généré (dans les commentaires) fournit un petit script de test qui utilise le [package RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) pour transmettre une instruction SQL à SQL Server, l’exécuter, puis récupérer son jeu de résultats sous forme de tramedonnées R. Vous pouvez supprimer les marques de commentaire de ce code de test pour écrire votre code R de manière interactive par rapport au jeu de résultats que vous obtenez à partir de SQL Server.

Le fichier *. Query.SQL* (*StoredProcedure.Query.sql* dans cet exemple) est l’endroit où vous écrivez et testez la requête SQL qui génère les données pour `InputDataSet`. Avec ce fichier *.sql*, l’éditeur vous fournit toutes les fonctionnalités Transact-SQL habituelles.

Une fois que vous êtes satisfait de votre code SQL, intégrez-le à votre code R en faisant glisser le fichier *.sql* sur l’éditeur ouvert pour le fichier *.R*. Dans l’image ci-dessous, *StoredProcedure.Query.sql* a été déplacé vers le point dans *StoredProcedure.R* après la virgule dans `sqlQuery(channel, )` :

![Lecture de fichier SQL dans une variable de chaîne R](media/sql-reference-sql-file-from-r.png)

Comme vous pouvez le voir, cette simple étape génère automatiquement le code R pour ouvrir le fichier *.sql*, lire son contenu dans une chaîne et le passer au package RODBC pour l’envoyer à SQL Server.

Vous pouvez maintenant écrire de manière interactive du code R qui manipule la tramedonnées `InputDataSet` comme vous le souhaitez. N’oubliez pas que vous pouvez simplement sélectionner le code R dans l’éditeur et l’envoyer à la [Fenêtre interactive](interactive-repl-for-r-in-visual-studio.md) en appuyant sur **Ctrl**+**Entrée**.

Enfin, le fichier *. Template.SQL* (*StoredProcedure.Template.sql* dans cet exemple) contient le modèle pour générer votre procédure stockée SQL :

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

- L’espace réservé `_RCODE_` est remplacé par le contenu du fichier *. R* (par exemple, *StoredProcedure.R*).
- L’espace réservé `_INPUT_QUERY_` est remplacé par le contenu du fichier *.Query.sql* (par exemple, *StoredProcedure.Query.sql*).
- Modifiez la clause `WITH RESULT SETS` pour décrire le schéma du jeu de résultats retourné par la procédure stockée. Identifiez spécifiquement les colonnes de la tramedonnées `OutputDataSet` que vous souhaitez retourner à l’appelant de la procédure stockée.

Par exemple, pour la requête suivante :

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Vous devez utiliser la clause `WITH RESULT SETS` suivante pour spécifier les types de données des valeurs de retour :

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publier une procédure stockée SQL

1. Sélectionnez la commande de menu publier les données des **Outils R**  >  **Data**  >  **avec options** .
1. Dans la boîte de dialogue qui s’affiche, remplacez **Publier sur** par **Base de données**, spécifiez la cible, sélectionnez **Publier**, et RTVS crée et publie la procédure stockée :

    ![Boîte de dialogue de publication de procédure stockée](media/sql-publish-with-options.png)

1. Pour publier toutes les procédures stockées dans un projet, vous pouvez utiliser la commande de publication des procédures stockées de données des **Outils R**  >  **Data**  >  **Publish Stored Procedures** , qui est également disponible quand vous cliquez avec le bouton droit sur le projet dans Explorateur de solutions.

> [!Tip]
> Si le Explorateur d’objets SQL Server s’ouvre dans Visual Studio, votre procédure stockée publiée apparaît dans le **Programmability**  >  dossier**procédures stockées** de programmabilité de votre base de données. Vous pouvez aussi l’exécuter à partir de l’Explorateur d’objets en cliquant avec le bouton droit et en sélectionnant **Exécuter la procédure**, ou en l’appelant de façon interactive à partir d’une fenêtre de requête *.sql*.
