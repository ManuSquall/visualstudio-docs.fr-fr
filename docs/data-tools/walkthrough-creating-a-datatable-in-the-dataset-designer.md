---
title: "Procédure pas à pas : Création d’un DataTable dans le Concepteur de Dataset | Documents Microsoft"
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: 0e1328eda7974b7e4ec04df0c4f5bd969cf09de6
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Procédure pas à pas : création d'un DataTable dans le Concepteur de DataSet
Cette procédure pas à pas explique comment créer un <xref:System.Data.DataTable> (sans TableAdapter) à l’aide de la **Concepteur de Dataset**. Pour plus d’informations sur la création de tables de données comprenant des TableAdapters, consultez [créer et configurer les TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un projet Application Windows Forms  
  
-   Ajout d’un nouveau jeu de données à l’application  
  
-   Ajout d’une nouvelle table de données au jeu de données  
  
-   Ajout de colonnes à la table de données  
  
-   Définition de la clé primaire pour la table  
  
## <a name="creating-a-new-windows-forms-application"></a>Création d’une Application Windows Forms  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>Pour créer un nouveau projet d’Application Windows Forms  
  
1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .  
  
2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **de bureau Windows classique**.  

3. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.  

4. Nommez le projet **DataTableWalkthrough**, puis choisissez **OK**. 
  
     Le **DataTableWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Ajout d’un nouveau jeu de données à l’Application  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Pour ajouter un nouvel élément dataset au projet  
  
1.  Sur le **projet** menu, sélectionnez **ajouter un nouvel élément...** .  
  
     La boîte de dialogue Ajouter un nouvel élément s’affiche.  
  
2.  Dans le volet gauche, sélectionnez **données**, puis sélectionnez **DataSet** dans le volet central.  
  
3.  Sélectionnez **Ajouter**.  
  
     Visual Studio ajoute un fichier appelé **DataSet1.xsd** au projet et l’ouvre dans le **Concepteur de Dataset**.  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>Ajout d’un nouveau DataTable au Dataset  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>Pour ajouter une nouvelle table de données au jeu de données  
  
1.  Faites glisser un **DataTable** à partir de la **DataSet** onglet de la **boîte à outils** sur la **Concepteur de Dataset**.  
  
     Une table nommée **DataTable1** est ajouté au jeu de données.  
   
2.  Cliquez sur la barre de titre de **DataTable1** et renommez-le `Music`.  
  
## <a name="adding-columns-to-the-data-table"></a>Ajout de colonnes à la Table de données  
  
#### <a name="to-add-columns-to-the-data-table"></a>Pour ajouter des colonnes à la table de données  
  
1.  Cliquez sur le **musique** table. Pointez sur **ajouter**, puis cliquez sur **colonne**.  
  
2.  Nom de la colonne `SongID`.  
  
3.  Dans le **propriétés** , configurez la <xref:System.Data.DataColumn.DataType%2A> propriété <xref:System.Int16?displayProperty=fullName>.  
  
4.  Répétez ce processus et ajoutez les colonnes suivantes :  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Définition de la clé primaire pour la Table  
Toutes les tables de données doivent avoir une clé primaire. Une clé primaire identifie de façon unique un enregistrement spécifique dans une table de données.  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>Pour définir la clé primaire de la table de données  
  
-   Cliquez sur le **SongID** colonne, puis cliquez sur **définir la clé primaire**.  
  
     Une icône de clé s’affiche en regard du **SongID** colonne.  
  
## <a name="saving-your-project"></a>L’enregistrement de votre projet  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>Pour enregistrer le projet DataTableWalkthrough  
  
-   Sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
## <a name="see-also"></a>Voir aussi
[Créer et configurer des datasets dans Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[Validation des données](../data-tools/validate-data-in-datasets.md)   
[Enregistrer des données](../data-tools/saving-data.md)   