---
title: Création et modification de Datasets typés | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vs.data.adddataset
dev_langs:
- VB
- CSharp
- C++
- aspx
- aspx
helpviewer_keywords:
- datasets [Visual Basic], visual designer
- data [Visual Studio], Dataset Designer
- Dataset Designer
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0147a114dff7144116e52f6fabe72f92e0885c4f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507722"
---
# <a name="creating-and-editing-typed-datasets"></a>Création et modification de Datasets typés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le**Concepteur de Dataset** est un ensemble d’outils visuels que vous pouvez utiliser pour créer et modifier des datasets typés et les éléments individuels qu’ils contiennent.  
  
 Le **Concepteur de Dataset** fournit des représentations visuelles des objets contenus dans les datasets typés. Vous créez et modifiez [TableAdapters](../data-tools/tableadapter-overview.md), [requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s, <xref:System.Data.DataColumn>s, et <xref:System.Data.DataRelation>s avec la **Concepteur de Dataset**.  
  
 Pour ouvrir le **Concepteur de Dataset**, double-cliquez sur un jeu de données dans **l’Explorateur de solutions**, ou sur un jeu de données dans le **des Sources de données** fenêtre et cliquez sur **modifier Jeu de données avec le concepteur**. Pour plus d’informations, consultez [Comment : ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3). Ajout d’une nouvelle <xref:System.Data.DataSet> un élément avec la **ajouter un nouvel élément** boîte de dialogue s’ouvre le **Concepteur de Dataset** avec un dataset vide prêt pour l’édition.  
  
> [!NOTE]
>  Le **Concepteur de Dataset** peut être utilisé pour étendre les fonctionnalités d’un jeu de données. Double-cliquez sur l’aire de conception ou avec le bouton droit et choisissez **afficher le Code** pour créer un fichier de classe partielle dans lequel vous pouvez ajouter du code au jeu de données qui ne sera pas modifié ou supprimé par le concepteur. Pour plus d’informations sur l’extension de la fonctionnalité d’un TableAdapter, consultez [étendent les fonctionnalités d’un TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 Le tableau suivant répertorie les tâches courantes que vous pouvez accomplir avec le **Concepteur de Dataset**.  
  
|À|Voir|  
|--------|---------|  
|Créer un TableAdapter|[Créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)|  
|Modifier un TableAdapter|[Comment : modifier des TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)|  
|Créer une requête TableAdapter|[Guide pratique pour créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)|  
|Modifier une requête TableAdapter|[Guide pratique pour modifier des requêtes TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Créer un <xref:System.Data.DataTable>|[Guide pratique pour créer des tables de données](../data-tools/how-to-create-data-tables.md)|  
|Modifier un <xref:System.Data.DataTable>|[Conception de DataTables](../data-tools/designing-datatables.md)|  
|Créer un <xref:System.Data.DataColumn>|[Comment : ajouter des colonnes à un DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)|  
|Créer une relation entre deux <xref:System.Data.DataTable>s|[Comment : créer des DataRelations avec le Concepteur de Dataset](http://msdn.microsoft.com/library/a3ab4803-0b50-4b74-9920-ab20bfbf1aa2)|  
|Étendre les fonctionnalités du jeu de données|[Comment : étendre les fonctionnalités d’un jeu de données](http://msdn.microsoft.com/library/dfbc21eb-7ea2-4942-addd-49677f5493be)|  
|Ajouter une validation à une table de données <xref:System.Data.DataTable.ColumnChanging> événement|[Comment : valider des données lors de la modification de colonne](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)|  
|Ajouter une validation à une table de données <xref:System.Data.DataTable.RowChanging> événement|[Comment : valider des données pendant les modifications de lignes](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)|  
  
## <a name="creating-objects-on-the-design-surface"></a>Création d’objets sur l’aire de conception  
 Vous pouvez créer des jeux de données en ajoutant et en modifiant les objets qui composent un jeu de données. Le tableau suivant fournit une explication des différents objets dans le **DataSet** onglet sur le **boîte à outils** qui peut être glissé sur l’aire de conception :  
  
|Object|Description|  
|------------|-----------------|  
|TableAdapter|Contient une collection de commandes de données et une connexion de données qui sont utilisés pour communiquer avec la base de données sous-jacente et remplir une table de données. Pour plus d’informations, consultez [vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md) et [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Query|Les requêtes TableAdapter sont des méthodes fortement typées qui exécutent des instructions SQL et les procédures stockées. Exécution d’une requête TableAdapter remplit une table de données avec des données ou effectue d’autres tâches de base de données. Pour plus d’informations, consultez [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md). Déplacement d’une requête sur une table d’ajoute la requête à cette table, alors que le glissement d’une requête dans une zone vide de la **Concepteur de Dataset** crée une requête globale. Pour plus d’informations, consultez [Comment : ajouter des requêtes globales à un TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Représente une collection en mémoire des lignes retournées à partir d’une base de données.|  
|Relation (<xref:System.Data.DataRelation>)|Représente une relation parent-enfant entre deux <xref:System.Data.DataTable>s. Pour plus d’informations, consultez [Introduction aux objets DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192) et [procédure pas à pas : création d’une relation entre les Tables de données](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82).|  
  
> [!NOTE]
>  Le **Concepteur de Dataset** se connecte à une base de données sous-jacente est créé uniquement lorsqu’un jeu de données ; le concepteur ne détecte pas automatiquement les modifications ultérieures apportées à la base de données. Pour actualiser un .xsd existant, exécutez de nouveau le **Assistant Configuration**. Si les relations de table ont changé, supprimez et rajoutez les tables appropriées pour le .xsd.  
  
## <a name="linq-to-dataset"></a>LINQ to Dataset  
 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] permet de [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) sur les données dans un <xref:System.Data.DataSet> objet. Pour plus d’informations, [consultez LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’un Dataset avec le Concepteur de Dataset](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Procédure pas à pas : Création d’un TableAdapter avec plusieurs requêtes](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Procédure pas à pas : Création d’un DataTable dans le Concepteur de Dataset](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Procédure pas à pas : Création d’une relation entre les Tables de données](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)   
 [Procédure pas à pas : Affichage de données sur un formulaire Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)