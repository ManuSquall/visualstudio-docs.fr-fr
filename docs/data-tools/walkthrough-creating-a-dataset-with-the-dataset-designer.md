---
title: "Procédure pas à pas : Création d’un Dataset avec le Concepteur de Dataset | Documents Microsoft"
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: f327d2010105c12c4b137317ed2406cae6cad9a3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Procédure pas à pas : création d'un groupe de données avec le Concepteur de DataSet
Dans cette procédure pas à pas, vous allez créer un jeu de données à l’aide de la **Concepteur de Dataset**. Il vous guidera le processus de création d’un projet et l’ajout d’un nouveau **DataSet** élément lui. Vous allez apprendre à créer des tables basées sur les tables dans une base de données sans utiliser d’Assistant.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un **Application Windows Forms** projet.  
  
-   Ajout de vide **DataSet** élément au projet.  
  
-   Création et configuration d’une source de données dans votre application en générant un dataset avec le **Concepteur de Dataset**.  
  
-   Création d’une connexion à la base de données Northwind **l’Explorateur de serveurs**.  
  
-   Création de tables avec des TableAdapters dans le jeu de données basée sur des tables dans la base de données.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Conditions préalables  
Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.  
  
1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement des éditions de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peut être installé dans le cadre de la **stockage de données et de traitement** charge de travail, ou sous la forme d’un composant individuel.  
  
2.  Installer la base de données Northwind en procédant comme suit :  

    1. Dans Visual Studio, ouvrez le **l’Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête...** .  

       Une fenêtre d’éditeur de requête s’ouvre.  

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.  

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.  

       Après une courte période, la requête est terminée et la base de données Northwind est créé.  
  
## <a name="creating-a-new-windows-forms-application-project"></a>Création d’un nouveau projet d’Application Windows Forms  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>Pour créer un nouveau projet d’Application Windows Forms  
  
1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .  
  
2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **de bureau Windows classique**.  

3. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.  

4. Nommez le projet **DatasetDesignerWalkthrough**, puis choisissez **OK**.  
  
     Visual Studio ajoute le projet **l’Explorateur de solutions** et afficher un nouveau formulaire dans le concepteur.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Ajout d’un nouveau jeu de données à l’Application  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Pour ajouter un nouvel élément dataset au projet  
  
1.  Sur le **projet** menu, sélectionnez **ajouter un nouvel élément...** .  
  
     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
2.  Dans le volet gauche, sélectionnez **données**, puis sélectionnez **DataSet** dans le volet central.  
  
3.  Nom du jeu de données **NorthwindDataset**, puis choisissez **ajouter**.  
  
     Visual Studio ajoute un fichier appelé **NorthwindDataset.xsd** au projet et l’ouvre dans le **Concepteur de Dataset**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Création d’une connexion de données dans l’Explorateur de serveurs  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Pour créer une connexion à la base de données Northwind  
  
1.  Sur le **vue** menu, cliquez sur **l’Explorateur de serveurs**.  
  
2.  Dans **l’Explorateur de serveurs**, cliquez sur le **se connecter à la base de données** bouton.  
  
3.  Créer une connexion à la base de données Northwind.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Création des Tables dans le jeu de données  
Cette section explique comment ajouter des tables au jeu de données.  
  
#### <a name="to-create-the-customers-table"></a>Pour créer la table Customers  
  
1.  Développez la connexion de données que vous avez créé dans **l’Explorateur de serveurs**, puis développez le **Tables** nœud.  
  
2.  Faites glisser le **clients** à partir de la table **l’Explorateur de serveurs** sur la **Concepteur de Dataset**.  
  
     A **clients** table de données et **CustomersTableAdapter** sont ajoutées au jeu de données.  
  
#### <a name="to-create-the-orders-table"></a>Pour créer la table Orders  
  
-   Faites glisser le **commandes** à partir de la table **l’Explorateur de serveurs** sur la **Concepteur de Dataset**.  
  
     Un **commandes** table de données, **OrdersTableAdapter**et la relation de données entre le **clients** et **commandes** tables sont ajoutées à la jeu de données.  
  
#### <a name="to-create-the-orderdetails-table"></a>Pour créer la table OrderDetails  
  
-   Faites glisser le **Order Details** à partir de la table **l’Explorateur de serveurs** sur la **Concepteur de Dataset**.  
  
     Un **Order Details** table de données, **OrderDetailsTableAdapter**et une relation de données entre le **commandes** et **OrderDetails** tables sont ajoutés au jeu de données.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
### <a name="to-add-functionality-to-your-application"></a>Pour ajouter une fonctionnalité à votre application  
  
-   Enregistrer le jeu de données.  
  
-   Sélectionnez des éléments dans le **des Sources de données** fenêtre et faites-les glisser jusqu'à un formulaire. Pour plus d’informations, consultez [des contrôles de lier des Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Ajoutez d’autres requêtes aux TableAdapters. 
  
-   Ajouter une logique de validation pour le <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> événements les tables de données dans le jeu de données. Pour plus d’informations, consultez [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Voir aussi
[Créer et configurer des datasets dans Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
[Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[Validation des données](../data-tools/validate-data-in-datasets.md)   
[Enregistrer des données](../data-tools/saving-data.md)