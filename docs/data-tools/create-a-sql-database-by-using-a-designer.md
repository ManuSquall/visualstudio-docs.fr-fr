---
title: Créez un fichier de base de données et utiliser le Concepteur de tables dans Visual Studio
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 53f34fbed4a2067836c5f2c7a8d4bf8aa6c09d29
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747038"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Créer une base de données et ajouter des tables dans Visual Studio
Vous pouvez utiliser Visual Studio pour créer et mettre à jour un fichier de base de données locale dans SQL Server Express LocalDB. Vous pouvez également créer une base de données en exécutant les instructions Transact-SQL dans le **l’Explorateur d’objets SQL Server** fenêtre outil dans Visual Studio. Dans cette rubrique, nous allons créer un fichier .mdf et ajouter des tables et des clés à l’aide du Concepteur de tables.

## <a name="prerequisites"></a>Prérequis
Pour effectuer cette procédure pas à pas, vous devez disposer facultatif **stockage de données et de traitement** la charge de travail installé dans Visual Studio. Pour l’installer, ouvrez **le programme d’installation de Visual Studio** et choisissez la **les charges de travail** onglet. Sous **Web & Cloud**, choisissez **stockage de données et de traitement**. Choisissez le **modifier** pour ajouter la charge de travail pour Visual Studio.

## <a name="create-a-project-and-a-local-database-file"></a>Créez un projet et un fichier de base de données locale

### <a name="to-create-a-project-and-a-database-file"></a>Pour créer un projet et un fichier de base de données
1.  Créez un projet Windows Forms nommé `SampleDatabaseWalkthrough`.

2.  Dans la barre de menus, sélectionnez **projet**, **ajouter un nouvel élément**.

3.  Dans la liste des modèles d’élément, faites défiler vers le bas et sélectionnez **base de données basée sur le Service**.

     ![Boîte de dialogue Modèles d'élément](../data-tools/media/raddata-vsitemtemplates.png)

4.  Nom de la base de données **SampleDatabase**, puis sélectionnez le **ajouter** bouton.

### <a name="to-add-a-data-source"></a>Pour ajouter une source de données
5.  Si le **des Sources de données** fenêtre n’est pas ouvert, ouvrez-le en sélectionnant le **Maj + Alt + D** clés ou, dans la barre de menus, en sélectionnant **vue**, **autres fenêtres**, **Des Sources de données**.

6.  Dans le **des Sources de données** fenêtre, sélectionnez le **ajouter une nouvelle Source de données** lien.

    Le **Assistant de Configuration de Source de données** s’ouvre.

7. Sur le **choisir un Type de Source de données** choisissez **base de données** , puis **suivant**.

8. Sur le **choisir un modèle de base de données** choisissez **suivant** pour accepter la valeur par défaut (Dataset).

9. Sur le **choisir votre connexion de données** page, sélectionnez le **SampleDatabase.mdf** de fichiers dans la liste déroulante, puis choisissez **suivant**.

10. Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration d’Application** choisissez **suivant**.

11. Un seul le **choisir vos objets de base de données** page, vous verrez un message indiquant que la base de données ne contient pas tous les objets. Choisissez **Terminer**.

### <a name="to-view-properties-of-the-data-connection"></a>Pour afficher les propriétés de la connexion de données
Vous pouvez afficher la chaîne de connexion pour le fichier SampleDatabase.mdf en ouvrant la fenêtre Propriétés de la connexion de données :

-   Dans Visual Studio, sélectionnez **vue**, **l’Explorateur d’objets SQL Server** si cette fenêtre n’est pas déjà ouverte. Ouvrez la fenêtre Propriétés en développant le **des connexions de données** nœud, ouvrez le menu contextuel de SampleDatabase.mdf, puis en sélectionnant **propriétés**.

-   Vous pouvez également sélectionner **vue**, **l’Explorateur de serveurs**, si cette fenêtre n’est pas déjà ouverte. Ouvrez la fenêtre Propriétés en développant le **des connexions de données** nœud. Ouvrez le menu contextuel de SampleDatabase.mdf, puis **propriétés**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Créer des tables et des clés à l’aide du Concepteur de tables
Dans cette section, vous allez créer deux tables, une clé primaire dans chaque table et quelques lignes d’exemples de données. Vous allez également créer une clé étrangère pour spécifier comment les enregistrements d’une table correspondent aux enregistrements de l’autre table.

### <a name="to-create-the-customers-table"></a>Pour créer la table Customers
1.  Dans **l’Explorateur de serveurs** ou **l’Explorateur d’objets SQL Server**, développez le **des connexions de données** nœud, puis développez le **SampleDatabase.mdf**nœud.

2.  Ouvrez le menu contextuel pour **Tables**, puis sélectionnez **ajouter une nouvelle Table**.

     Le **Concepteur de tables** s’ouvre et affiche une grille avec une ligne par défaut, ce qui représente une seule colonne dans la table que vous êtes en train de créer. En ajoutant des lignes à la grille, vous définissez des colonnes supplémentaires dans la table.

3.  Dans la grille, ajoutez une ligne pour chaque entrée suivante :

    |Nom de la colonne|Type de données|Null autorisé|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (désactivé)|
    |`CompanyName`|`nvarchar(50)`|False (désactivé)|
    |`ContactName`|`nvarchar (50)`|True (sélectionné)|
    |`Phone`|`nvarchar (24)`|True (sélectionné)|

4.  Ouvrez le menu contextuel pour le `CustomerID` de ligne, puis sélectionnez **définir la clé primaire**.

5.  Ouvrez le menu contextuel pour la ligne par défaut, puis **supprimer**.

6.  Nommez la table Customers en mettant à jour la première ligne du volet de script afin qu'elle corresponde à l'exemple suivant :

    ```sql
    CREATE TABLE [dbo].[Customers]
    ```

    Vous devez voir quelque chose de similaire à :

    ![Concepteur de tables](../data-tools/media/raddata-table-designer.png)

7.  Dans le coin supérieur gauche de la **Concepteur de tables**, sélectionnez le **mise à jour** bouton.

8.  Dans le **mises à jour de la base de données aperçu** boîte de dialogue, sélectionnez le **mise à jour de la base de données** bouton.

    Vos modifications sont enregistrées dans le fichier de base de données local.

### <a name="to-create-the-orders-table"></a>Pour créer la table Orders
1.  Ajoutez une table, puis ajoutez une ligne pour chaque entrée dans le tableau suivant :

    |Nom de la colonne|Type de données|Null autorisé|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (désactivé)|
    |`CustomerID`|`nchar(5)`|False (désactivé)|
    |`OrderDate`|`datetime`|True (sélectionné)|
    |`OrderQuantity`|`int`|True (sélectionné)|

2.  Définissez **OrderID** comme clé primaire, puis supprimez la ligne par défaut.

3.  Nommez la table Orders en mettant à jour la première ligne du volet de script afin qu'elle corresponde à l'exemple suivant :

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4.  Dans le coin supérieur gauche de la **Concepteur de tables**, sélectionnez le **mise à jour** bouton.

5.  Dans le **mises à jour de la base de données aperçu** boîte de dialogue, sélectionnez le **mise à jour de la base de données** bouton.

    Vos modifications sont enregistrées dans le fichier de base de données local.

### <a name="to-create-a-foreign-key"></a>Pour créer une clé étrangère
1.  Dans le volet contextuel sur le côté droit de la grille, ouvrez le menu contextuel de **clés étrangères**, puis sélectionnez **ajouter une nouvelle clé étrangère**, comme le montre l’illustration suivante.

     ![Ajout d'une clé étrangère dans le concepteur de tables](../data-tools/media/foreignkey.png)

2.  Dans la zone de texte qui apparaît, remplacez **ToTable** avec `Customers`.

3.  Dans le volet de T-SQL, mettez à jour la dernière ligne pour correspondre à l’exemple suivant :

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4.  Dans le coin supérieur gauche de la **Concepteur de tables**, sélectionnez le **mise à jour** bouton.

5.  Dans le **mises à jour de la base de données aperçu** boîte de dialogue, sélectionnez le **mise à jour de la base de données** bouton.

    Vos modifications sont enregistrées dans le fichier de base de données local.

## <a name="populate-the-tables-with-data"></a>Remplir les tables de données

### <a name="to-populate-the-tables-with-data"></a>Pour remplir les tables avec des données

1.  Dans **l’Explorateur de serveurs** ou **l’Explorateur d’objets SQL Server**, développez le nœud de la base de données.

2.  Ouvrez le menu contextuel pour le **Tables** nœud, sélectionnez **Actualiser**, puis développez le **Tables** nœud.

3.  Ouvrez le menu contextuel pour la table Customers et sélectionnez **afficher les données de Table**.

4.  Ajoutez les données voulues pour certains clients.

    Vous pouvez spécifier cinq caractères de votre choix comme ID de client, mais choisissez-en au moins un que vous pouvez mémoriser pour l'utiliser ultérieurement dans cette procédure.

5.  Ouvrez le menu contextuel de la table Orders, puis **afficher les données de Table**.

6.  Ajouter des données pour certaines commandes.

    > [!IMPORTANT]
    > Assurez-vous que tous les ID de commande et quantités commandées sont des entiers et que chaque ID de client correspond à une valeur que vous avez spécifié dans la colonne CustomerID de la table Customers.

7.  Dans la barre de menus, sélectionnez **fichier**, **Enregistrer tout**.

## <a name="see-also"></a>Voir aussi

- [Accès aux données dans Visual Studio](accessing-data-in-visual-studio.md)