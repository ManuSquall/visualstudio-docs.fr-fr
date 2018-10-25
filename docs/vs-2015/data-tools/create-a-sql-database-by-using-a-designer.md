---
title: Créer une base de données SQL à l’aide d’un concepteur | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0ef261ec4ea803dcfc42b6151a5c828d5b03811a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860327"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Créer une base de données SQL à l’aide d’un concepteur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Vous pouvez explorer les tâches de base, telles que l’ajout de tables et définition des colonnes, à l’aide de Visual Studio pour créer et mettre à jour un fichier de base de données locale dans SQL Server Express LocalDB. Après avoir terminé cette procédure pas à pas, vous pouvez découvrir des fonctionnalités plus avancées en utilisant votre base de données locale comme point de départ d'autres procédures pas à pas qui en ont besoin.  
  
 Vous pouvez également créer une base de données à l’aide de SQL Server Management Studio (un téléchargement distinct) ou des instructions Transact-SQL dans le **Explorateur d’objets SQL Server** fenêtre outil dans Visual Studio.  
  
 Au cours de cette procédure, vous exécuterez les tâches suivantes :  
  
-   [Créer un projet et un fichier de base de données locale](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)  
  
-   [Créer des tables, colonnes, clés primaires et les clés étrangères](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)  
  
-   [Remplir les tables de données](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure pas à pas, vérifiez que vous avez installé SQL Server Data Tools. Sur le **vue** menu, vous devez voir **Explorateur d’objets SQL Server**. Si elle n’y ne figure pas, accédez à **Ajout / Suppression de programmes**, cliquez sur **Visual Studio 2015**, sélectionnez **modification**, activez la case à côté **deSQLServerDataTools**.  
  
##  <a name="BKMK_CreateNewSQLDB"></a> Créer un projet et un fichier de base de données locale  
  
#### <a name="to-create-a-project-and-a-database-file"></a>Pour créer un projet et un fichier de base de données  
  
1. Créer un projet Windows Forms qui est nommé `SampleDatabaseWalkthrough`.  
  
2. Dans la barre de menus, sélectionnez **projet** > **ajouter un nouvel élément**.  
  
3. Dans la liste des modèles d’élément, faites défiler vers le bas et sélectionnez **base de données basée sur le Service**.  
  
    ![Boîte de dialogue Modèles élément](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")  
  
4. Nom de la base de données **SampleDatabase**, puis sélectionnez le **ajouter** bouton.  
  
5. Si le **des Sources de données** fenêtre n’est pas ouverte, ouvrez-le en sélectionnant les touches Maj + Alt + D ou, sur la barre de menus, en sélectionnant **vue** > **Windows autres**  >  **Des Sources de données**.  
  
6. Dans le **des Sources de données** fenêtre, sélectionnez le **ajouter une nouvelle Source de données** lien.  
  
7. Dans le **Assistant de Configuration de Source de données**, sélectionnez le **suivant** quatre fois pour accepter les paramètres par défaut, puis sélectionnez le **Terminer** bouton.  
  
   En ouvrant la fenêtre de propriétés pour la base de données, vous pouvez consulter la chaîne de connexion et l'emplacement du fichier principal .mdf. Vous verrez que le fichier de base de données est dans le dossier du projet.  
  
-   Dans Visual Studio, sélectionnez **vue** > **Explorateur d’objets SQL Server** si cette fenêtre n’est pas déjà ouverte. Ouvrez la fenêtre Propriétés en développant le **des connexions de données** nœud, ouvrez le menu contextuel de SampleDatabase.mdf, puis en sélectionnant **propriétés**.  
  
-   Vous pouvez également sélectionner **vue** > **Explorateur de serveurs**, si cette fenêtre n’est pas déjà ouverte. Ouvrez la fenêtre Propriétés en développant le **des connexions de données** nœud. Ouvrez le menu contextuel de SampleDatabase.mdf, puis sélectionnez **propriétés**.  
  
##  <a name="BKMK_CreateNewTbls"></a> Créer des tables, colonnes, clés primaires et les clés étrangères  
 Dans cette section, vous créerez des tables, une clé primaire dans chaque table, et quelques lignes d'exemples de données. La procédure suivante vous donnera une idée de la façon dont ces informations peuvent apparaître dans une application. Vous créerez également une clé étrangère pour spécifier comment les enregistrements d'une table peuvent correspondre aux enregistrements de l'autre table.  
  
#### <a name="to-create-the-customers-table"></a>Pour créer la table Customers  
  
1.  Dans **Explorateur de serveurs** ou **Explorateur d’objets SQL Server**, développez le **des connexions de données** nœud, puis développez le **SampleDatabase.mdf**nœud.  
  
2.  Ouvrez le menu contextuel pour **Tables**, puis sélectionnez **ajouter une nouvelle Table**.  
  
     Le **Concepteur de tables** s’ouvre et affiche une grille avec une ligne par défaut, qui représente une seule colonne dans la table que vous créez. En ajoutant des lignes à la grille, vous définissez des colonnes supplémentaires dans la table.  
  
3.  Dans la grille, ajoutez une ligne pour chaque entrée suivante :  
  
    |Nom de la colonne|Type de données|Null autorisé|  
    |-----------------|---------------|-----------------|  
    |`CustomerID`|`nchar(5)`|False (désactivé)|  
    |`CompanyName`|`nvarchar(50)`|False (désactivé)|  
    |`ContactName`|`nvarchar (50)`|True (sélectionné)|  
    |`Phone`|`nvarchar (24)`|True (sélectionné)|  
  
4.  Ouvrez le menu contextuel pour le `CustomerID` de ligne, puis sélectionnez **définir la clé primaire**.  
  
5.  Ouvrez le menu contextuel pour la ligne par défaut, puis sélectionnez **supprimer**.  
  
6.  Nommez la table Customers en mettant à jour la première ligne du volet de script afin qu'elle corresponde à l'exemple suivant :  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
     Vous devez voir quelque chose de similaire à :  
  
     ![Concepteur de tables](../data-tools/media/raddata-table-designer.png "raddata Concepteur de tables")  
  
7.  Dans le coin supérieur gauche de la **Concepteur de tables**, sélectionnez le **mise à jour** bouton.  
  
8.  Dans le **mises à jour de la base de données aperçu** boîte de dialogue, sélectionnez le **mise à jour la base de données** bouton.  
  
     Vos modifications sont enregistrées dans le fichier de base de données local.  
  
#### <a name="to-create-the-orders-table"></a>Pour créer la table Orders  
  
1.  Ajoutez une table, puis ajoutez une ligne pour chaque entrée dans le tableau suivant :  
  
    |Nom de la colonne|Type de données|Null autorisé|  
    |-----------------|---------------|-----------------|  
    |`OrderID`|`int`|False (désactivé)|  
    |`CustomerID`|`nchar(5)`|False (désactivé)|  
    |`OrderDate`|`datetime`|True (sélectionné)|  
    |`OrderQuantity`|`int`|True (sélectionné)|  
  
2.  Définissez **OrderID** comme clé primaire, puis supprimez la ligne par défaut.  
  
3.  Nommez la table Orders en mettant à jour la première ligne du volet de script afin qu'elle corresponde à l'exemple suivant :  
  
    ```  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4.  Dans le coin supérieur gauche de la **Concepteur de tables**, sélectionnez le **mise à jour** bouton.  
  
5.  Dans le **mises à jour de la base de données aperçu** boîte de dialogue, sélectionnez le **mise à jour la base de données** bouton.  
  
     Vos modifications sont enregistrées dans le fichier de base de données local.  
  
#### <a name="to-create-a-foreign-key"></a>Pour créer une clé étrangère  
  
1.  Dans le volet contextuel sur le côté droit de la grille, ouvrez le menu contextuel pour **clés étrangères**, puis sélectionnez **ajouter une nouvelle clé étrangère**, comme le montre l’illustration suivante.  
  
     ![Ajout d’une clé étrangère dans le Concepteur de tables](../data-tools/media/foreignkey.png "ForeignKey")  
  
2.  Dans la zone de texte qui s’affiche, remplacez **ToTable** avec `Customers`.  
  
3.  Dans le volet T-SQL, mettez à jour la dernière ligne pour correspondre à l’exemple suivant :  
  
    ```  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4.  Dans le coin supérieur gauche de la **Concepteur de tables**, sélectionnez le **mise à jour** bouton.  
  
5.  Dans le **mises à jour de la base de données aperçu** boîte de dialogue, sélectionnez le **mise à jour la base de données** bouton.  
  
     Vos modifications sont enregistrées dans le fichier de base de données local.  
  
##  <a name="BKMK_Populating"></a> Remplir les tables de données  
  
#### <a name="to-populate-the-tables-with-data"></a>Pour remplir les tables avec des données  
  
1.  Dans **Explorateur de serveurs** ou **Explorateur d’objets SQL Server**, développez le nœud de la base de données.  
  
2.  Ouvrez le menu contextuel pour le **Tables** nœud, sélectionnez **Actualiser**, puis développez le **Tables** nœud.  
  
3.  Ouvrez le menu contextuel pour la table Customers, puis sélectionnez **afficher les données de Table**.  
  
4.  Ajoutez les données voulues pour au moins trois clients.  
  
     Vous pouvez spécifier cinq caractères de votre choix comme ID de client, mais choisissez-en au moins un que vous pouvez mémoriser pour l'utiliser ultérieurement dans cette procédure.  
  
5.  Ouvrez le menu contextuel de la table Orders, puis sélectionnez **afficher les données de Table**.  
  
6.  Ajoutez des données pour au moins trois commandes.  
  
    > [!IMPORTANT]
    >  Vérifiez que tous les ID de commande et quantités commandées sont des entiers et que chaque ID client correspond à une valeur que vous avez spécifiée dans la colonne CustomerID de la table Customers.  
  
7.  Dans la barre de menus, sélectionnez **fichier** > **Enregistrer tout**.  
  
8.  Dans la barre de menus, sélectionnez **fichier** > **fermer la Solution**.  
  
    > [!NOTE]
    >  Il est recommandé de sauvegarder le fichier de base de données que vous venez de créer en copiant et en collant la copie dans un autre emplacement ou en renommant la copie.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez un fichier de base de données locale avec des exemples de données, vous pouvez effectuer une des procédures pas à pas montrent comment effectuer les tâches de base de données.

