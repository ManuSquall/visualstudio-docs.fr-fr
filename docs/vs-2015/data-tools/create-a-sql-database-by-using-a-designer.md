---
title: Créer une base de données SQL à l’aide d’un concepteur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 33b97050f04fd23a9fa3b6c3c641faa5dfe4802f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651059"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Créer une base de données SQL à l’aide d’un concepteur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez explorer les tâches de base, telles que l’ajout de tables et la définition de colonnes, à l’aide de Visual Studio pour créer et mettre à jour un fichier de base de données local dans SQL Server Express base de données locale. Après avoir terminé cette procédure pas à pas, vous pouvez découvrir des fonctionnalités plus avancées en utilisant votre base de données locale comme point de départ d'autres procédures pas à pas qui en ont besoin.

 Vous pouvez également créer une base de données à l’aide d’SQL Server Management Studio (un téléchargement distinct) ou d’instructions Transact-SQL dans la fenêtre outil **Explorateur d’objets SQL Server** dans Visual Studio.

 Au cours de cette procédure, vous exécuterez les tâches suivantes :

- [Créer un projet et un fichier de base de données local](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)

- [Créer des tables, des colonnes, des clés primaires et des clés étrangères](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)

- [Remplir les tables avec des données](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)

## <a name="prerequisites"></a>Configuration requise
 Pour effectuer cette procédure pas à pas, assurez-vous que SQL Server Data Tools est installé. Dans le menu **affichage** , vous devriez voir **Explorateur d’objets SQL Server**. Si ce n’est pas le cas, accédez à **Ajout/suppression de programmes**, cliquez sur **Visual Studio 2015**, sélectionnez **modifier**, puis activez la case à cocher en regard de **SQL Server Data Tools**.

## <a name="BKMK_CreateNewSQLDB"></a>Créer un projet et un fichier de base de données local

#### <a name="to-create-a-project-and-a-database-file"></a>Pour créer un projet et un fichier de base de données

1. Créez un projet Windows Forms nommé `SampleDatabaseWalkthrough`.

2. Dans la barre de menus, sélectionnez **projet**  > **Ajouter un nouvel élément**.

3. Dans la liste des modèles d’élément, faites défiler vers le dessous et sélectionnez **base de données basée sur les services**.

    ![Modèles d’élément, boîte de dialogue](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")

4. Nommez la base de données **SampleDatabase**, puis sélectionnez le bouton **Ajouter** .

5. Si la fenêtre **sources de données** n’est pas ouverte, ouvrez-la en sélectionnant les touches Maj + Alt + D ou, dans la barre de menus, en sélectionnant **Afficher**  >  d’autres**sources de données** **Windows**  > .

6. Dans la fenêtre **sources de données** , sélectionnez le lien ajouter une **nouvelle source de données** .

7. Dans l **'Assistant Configuration de source de données**, sélectionnez le bouton **suivant** quatre fois pour accepter les paramètres par défaut, puis sélectionnez le bouton **Terminer** .

   En ouvrant la fenêtre de propriétés pour la base de données, vous pouvez consulter la chaîne de connexion et l'emplacement du fichier principal .mdf. Vous verrez que le fichier de base de données se trouve dans le dossier du projet.

- Dans Visual Studio, sélectionnez **afficher**  > **Explorateur d’objets SQL Server** si cette fenêtre n’est pas déjà ouverte. Ouvrez la fenêtre Propriétés en développant le nœud **connexions de données** , en ouvrant le menu contextuel pour SampleDatabase. mdf, puis en sélectionnant **Propriétés**.

- Vous pouvez également sélectionner **afficher**  > **Explorateur de serveurs**si cette fenêtre n’est pas déjà ouverte. Ouvrez la fenêtre Propriétés en développant le nœud **connexions de données** . Ouvrez le menu contextuel pour SampleDatabase. mdf, puis sélectionnez **Propriétés**.

## <a name="BKMK_CreateNewTbls"></a>Créer des tables, des colonnes, des clés primaires et des clés étrangères
 Dans cette section, vous créerez des tables, une clé primaire dans chaque table, et quelques lignes d'exemples de données. La procédure suivante vous donnera une idée de la façon dont ces informations peuvent apparaître dans une application. Vous créerez également une clé étrangère pour spécifier comment les enregistrements d'une table peuvent correspondre aux enregistrements de l'autre table.

#### <a name="to-create-the-customers-table"></a>Pour créer la table Customers

1. Dans **Explorateur de serveurs** ou **Explorateur d’objets SQL Server**, développez le nœud **connexions de données** , puis développez le nœud **SampleDatabase. mdf** .

2. Ouvrez le menu contextuel pour les **tables**, puis sélectionnez **Ajouter une nouvelle table**.

     Le **Concepteur de tables** s’ouvre et affiche une grille avec une ligne par défaut, qui représente une seule colonne de la table que vous créez. En ajoutant des lignes à la grille, vous définissez des colonnes supplémentaires dans la table.

3. Dans la grille, ajoutez une ligne pour chaque entrée suivante :

    |Nom de la colonne|Type de données|Null autorisé|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (désactivé)|
    |`CompanyName`|`nvarchar(50)`|False (désactivé)|
    |`ContactName`|`nvarchar (50)`|True (sélectionné)|
    |`Phone`|`nvarchar (24)`|True (sélectionné)|

4. Ouvrez le menu contextuel de la ligne `CustomerID`, puis sélectionnez **définir la clé primaire**.

5. Ouvrez le menu contextuel de la ligne par défaut, puis sélectionnez **supprimer**.

6. Nommez la table Customers en mettant à jour la première ligne du volet de script afin qu'elle corresponde à l'exemple suivant :

    ```
    CREATE TABLE [dbo].[Customers]
    ```

     Vous devez voir quelque chose de similaire à :

     ![Concepteur de tables](../data-tools/media/raddata-table-designer.png "raddata Concepteur de tables")

7. Dans l’angle supérieur gauche de la **Concepteur de tables**, sélectionnez le bouton **mettre à jour** .

8. Dans la boîte de dialogue **aperçu des mises à jour de la base de données** , sélectionnez le bouton **mettre à jour la base de données** .

     Vos modifications sont enregistrées dans le fichier de base de données local.

#### <a name="to-create-the-orders-table"></a>Pour créer la table Orders

1. Ajoutez une table, puis ajoutez une ligne pour chaque entrée dans le tableau suivant :

    |Nom de la colonne|Type de données|Null autorisé|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (désactivé)|
    |`CustomerID`|`nchar(5)`|False (désactivé)|
    |`OrderDate`|`datetime`|True (sélectionné)|
    |`OrderQuantity`|`int`|True (sélectionné)|

2. Définissez **OrderID** comme clé primaire, puis supprimez la ligne par défaut.

3. Nommez la table Orders en mettant à jour la première ligne du volet de script afin qu'elle corresponde à l'exemple suivant :

    ```
    CREATE TABLE [dbo].[Orders]
    ```

4. Dans l’angle supérieur gauche de la **Concepteur de tables**, sélectionnez le bouton **mettre à jour** .

5. Dans la boîte de dialogue **aperçu des mises à jour de la base de données** , sélectionnez le bouton **mettre à jour la base de données** .

     Vos modifications sont enregistrées dans le fichier de base de données local.

#### <a name="to-create-a-foreign-key"></a>Pour créer une clé étrangère

1. Dans le volet contextuel à droite de la grille, ouvrez le menu contextuel pour les **clés étrangères**, puis sélectionnez **Ajouter une nouvelle clé étrangère**, comme le montre l’illustration suivante.

     ![Ajout d’une clé étrangère dans Concepteur de tables](../data-tools/media/foreignkey.png "ForeignKey")

2. Dans la zone de texte qui s’affiche, remplacez **ToTable** par `Customers`.

3. Dans le volet T-SQL, mettez à jour la dernière ligne pour qu’elle corresponde à l’exemple suivant :

    ```
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. Dans l’angle supérieur gauche de la **Concepteur de tables**, sélectionnez le bouton **mettre à jour** .

5. Dans la boîte de dialogue **aperçu des mises à jour de la base de données** , sélectionnez le bouton **mettre à jour la base de données** .

     Vos modifications sont enregistrées dans le fichier de base de données local.

## <a name="BKMK_Populating"></a>Remplir les tables avec des données

#### <a name="to-populate-the-tables-with-data"></a>Pour remplir les tables avec des données

1. Dans **Explorateur de serveurs** ou **Explorateur d’objets SQL Server**, développez le nœud de l’exemple de base de données.

2. Ouvrez le menu contextuel du nœud **tables** , sélectionnez **Actualiser**, puis développez le nœud **tables** .

3. Ouvrez le menu contextuel de la table Customers, puis sélectionnez **afficher les données**de la table.

4. Ajoutez les données voulues pour au moins trois clients.

     Vous pouvez spécifier cinq caractères de votre choix comme ID de client, mais choisissez-en au moins un que vous pouvez mémoriser pour l'utiliser ultérieurement dans cette procédure.

5. Ouvrez le menu contextuel de la table Orders, puis sélectionnez **afficher les données**de la table.

6. Ajoutez des données pour au moins trois commandes.

    > [!IMPORTANT]
    > Vérifiez que tous les ID de commande et quantités commandées sont des entiers et que chaque ID client correspond à une valeur que vous avez spécifiée dans la colonne CustomerID de la table Customers.

7. Dans la barre de menus, sélectionnez **fichier**  > **enregistrer tout**.

8. Dans la barre de menus, sélectionnez **fichier**  > **Fermer la solution**.

    > [!NOTE]
    > Il est recommandé de sauvegarder le fichier de base de données que vous venez de créer en copiant et en collant la copie dans un autre emplacement ou en renommant la copie.

## <a name="next-steps"></a>Étapes suivantes
 Maintenant que vous disposez d’un fichier de base de données local avec quelques exemples de données, vous pouvez effectuer les procédures pas à pas qui illustrent les tâches de base de données.
