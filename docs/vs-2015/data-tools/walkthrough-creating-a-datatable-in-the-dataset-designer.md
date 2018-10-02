---
title: 'Procédure pas à pas : Création d’un DataTable dans le Concepteur de Dataset | Microsoft Docs'
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
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 832dba200fca438d000bae101381389ea20cfb17
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496331"
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Procédure pas à pas : création d'un DataTable dans le Concepteur de DataSet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas explique comment créer un <xref:System.Data.DataTable> (sans TableAdapter) à l’aide de la **Concepteur de Dataset**. Pour plus d’informations sur la création de tables de données comprenant des TableAdapters, consultez [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un nouveau projet d’Application de Windows  
  
-   Ajout d’un nouveau jeu de données à l’application  
  
-   Ajout d’une nouvelle table de données au jeu de données  
  
-   Ajouter des colonnes dans la table de données  
  
-   Définition de la clé primaire pour la table  
  
## <a name="creating-a-new-windows-application"></a>Création d'une application Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Pour créer le projet d'application Windows  
  
1.  À partir de la **fichier** menu, créez un nouveau projet.  
  
2.  Choisissez un langage de programmation dans le **Types de projets** volet.  
  
3.  Cliquez sur **Windows Application** dans le **modèles** volet.  
  
4.  Nommez le projet `DataTableWalkthrough`, puis cliquez sur **OK**.  
  
     Visual Studio ajoute le projet à **l’Explorateur de solutions** et affiche **Form1** dans le concepteur.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Ajout d’un nouveau jeu de données à l’Application  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Pour ajouter un nouvel élément de jeu de données au projet  
  
1.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
     La boîte de dialogue Ajouter un nouvel élément s’affiche.  
  
2.  Dans le **modèles** boîte, sélectionnez **DataSet**.  
  
3.  Cliquez sur **Ajouter**.  
  
     Visual Studio ajoute un fichier appelé **DataSet1.xsd** au projet et ouvrez-le dans le **Concepteur de Dataset**.  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>Ajout d’un nouveau DataTable au Dataset  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>Pour ajouter une nouvelle table de données au jeu de données  
  
1.  Faites glisser un **DataTable** à partir de la **DataSet** onglet de la **boîte à outils** sur le **Concepteur de Dataset**.  
  
     Une table nommée **DataTable1** est ajouté au jeu de données.  
  
    > [!NOTE]
    >  Pour créer une table de données qui comprend un TableAdapter, consultez [procédure pas à pas : création d’un TableAdapter avec plusieurs requêtes](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Cliquez sur la barre de titre de **DataTable1** et renommez-le `Music`.  
  
## <a name="adding-columns-to-the-data-table"></a>Ajouter des colonnes dans la Table de données  
  
#### <a name="to-add-columns-to-the-data-table"></a>Pour ajouter des colonnes à la table de données  
  
1.  Cliquez sur le **musique** table. Pointez sur **ajouter**, puis cliquez sur **colonne**.  
  
2.  Nom de la colonne `SongID`.  
  
3.  Dans le **propriétés** fenêtre, définissez la <xref:System.Data.DataColumn.DataType%2A> propriété <xref:System.Int16?displayProperty=fullName>.  
  
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
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez créé la table, vous souhaiterez effectuer l’une des actions suivantes :  
  
|À|Voir|  
|--------|---------|  
|Créer un formulaire d’entrée de données|[Procédure pas à pas : Affichage de données sur un formulaire Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Ajouter des données à la table|[Ajout de données à un DataTable](http://msdn.microsoft.com/library/d6aa8474-7bde-48f7-949d-20dc38a1625b).|  
|Afficher les données dans une table|[Affichage des données dans un DataTable](http://msdn.microsoft.com/library/1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc).|  
|Modifier des données|[Modifications de DataTable](http://msdn.microsoft.com/library/f08008a9-042e-4de9-94f3-4f0e502b1eb5)|  
|Supprimer une ligne d’une table|[Suppression de DataRow](http://msdn.microsoft.com/library/c34f531d-4b9b-4071-b2d7-342c402aa586)|  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [L’enregistrement des données](../data-tools/saving-data.md)   
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)