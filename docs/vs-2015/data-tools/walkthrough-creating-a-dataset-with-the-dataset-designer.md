---
title: 'Procédure pas à pas : Création d’un Dataset avec le Concepteur de Dataset | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7c17a93a5d250ce620c37a2a0a89472bf760750b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502215"
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Procédure pas à pas : création d'un groupe de données avec le Concepteur de DataSet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous allez créer un jeu de données à l’aide de la **Concepteur de Dataset**. Il décriront le processus de création d’un projet et l’ajout d’une nouvelle **DataSet** élément à ce dernier. Vous allez apprendre à créer des tables basées sur les tables dans une base de données sans utiliser l’Assistant.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un nouveau **Windows Application** projet.  
  
-   Ajout de vide **DataSet** élément au projet.  
  
-   Création et configuration d’une source de données dans votre application en générant un dataset avec le **Concepteur de Dataset**.  
  
-   Création d’une connexion à la base de données Northwind dans **Explorateur de serveurs**.  
  
-   Création de tables avec les TableAdapters dans le jeu de données basée sur des tables dans la base de données.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Accès à l'exemple de base de données Northwind (vers SQL Server ou Access). Pour plus d’informations, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application-project"></a>Création d’un nouveau projet d’Application Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Pour créer le projet d'application Windows  
  
1.  À partir de la **fichier** menu, créez un nouveau projet.  
  
2.  Choisissez un langage de programmation dans le **Types de projets** volet.  
  
3.  Cliquez sur **Windows Application** dans le **modèles** volet.  
  
4.  Nommez le projet `DatasetDesignerWalkthrough`, puis cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ajoute le projet à **l’Explorateur de solutions** et afficher un nouveau formulaire dans le concepteur.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Ajout d’un nouveau jeu de données à l’Application  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Pour ajouter un nouvel élément de jeu de données au projet  
  
1.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
2.  Dans le **modèles** zone de la **ajouter un nouvel élément** boîte de dialogue, cliquez sur **DataSet**.  
  
3.  Nommez le jeu de données `NorthwindDataset`, puis cliquez sur **ajouter**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ajoute un fichier appelé **NorthwindDataset.xsd** au projet et ouvrez-le dans le **Concepteur de Dataset**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Création d’une connexion de données dans l’Explorateur de serveurs  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Pour créer une connexion à la base de données Northwind  
  
1.  Sur le **vue** menu, cliquez sur **Explorateur de serveurs**.  
  
2.  Dans **Explorateur de serveurs**, cliquez sur le **se connecter à la base de données** bouton.  
  
3.  Créer une connexion à la base de données Northwind.  
  
    > [!NOTE]
    >  Vous pouvez vous connecter à la version de SQL Server ou Access de Northwind pour cette procédure pas à pas.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Création des Tables dans le jeu de données  
 Cette section explique comment ajouter des tables au jeu de données.  
  
#### <a name="to-create-the-customers-table"></a>Pour créer la table Customers  
  
1.  Développez la connexion de données que vous avez créé dans **Explorateur de serveurs**, puis développez le **Tables** nœud.  
  
2.  Faites glisser le **clients** à partir de la table **Explorateur de serveurs** sur le **Concepteur de Dataset**.  
  
     Un **clients** table de données et **CustomersTableAdapter** sont ajoutées au jeu de données.  
  
#### <a name="to-create-the-orders-table"></a>Pour créer la table Orders  
  
-   Faites glisser le **commandes** à partir de la table **Explorateur de serveurs** sur le **Concepteur de Dataset**.  
  
     Un **commandes** table de données, **OrdersTableAdapter**et la relation de données entre le **clients** et **commandes** tables sont ajoutées à la jeu de données.  
  
#### <a name="to-create-the-orderdetails-table"></a>Pour créer la table OrderDetails  
  
-   Faites glisser le **Order Details** à partir de la table **Explorateur de serveurs** sur le **Concepteur de Dataset**.  
  
     Un **Order Details** table de données, **Order DetailsTableAdapter**et une relation de données entre le **commandes** et **Order Details** tables sont ajoutés au jeu de données.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
### <a name="to-add-functionality-to-your-application"></a>Pour ajouter une fonctionnalité à votre application  
  
-   Enregistrer le jeu de données.  
  
-   Sélectionnez des éléments dans le **des Sources de données** fenêtre et faites-les glisser jusqu'à un formulaire. Pour plus d’informations, consultez [lier les formulaires Windows contrôle aux données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Ajoutez davantage de requêtes pour les TableAdapters. Pour plus d’informations, consultez [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Ajouter une logique de validation pour le <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> événements les tables de données dans le jeu de données. Pour plus d’informations, consultez [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)