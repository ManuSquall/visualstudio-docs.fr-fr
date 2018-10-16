---
title: 'Comment : créer des Tables de données | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], creating data tables
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8b26bf0cfbd387f33f9f038d5927db795a8f2769
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288910"
---
# <a name="how-to-create-data-tables"></a>Comment : créer des tables de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Données peuvent être stockées en mémoire dans <xref:System.Data.DataTable> objets. (Jeux de données est constituées de <xref:System.Data.DataTable> objets.) Vous créez généralement de nouvelles tables avec les TableAdapters à l’aide du [Assistant Configuration de TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) ou en faisant glisser des objets de base de données à partir de **Explorateur de serveurs** sur la **Concepteur de Dataset** .  
  
 Tables de données sont créées comme un sous-produit lorsque vous créez des TableAdapters dans le [Assistant de Configuration de Source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) également, mais elles peuvent également être créées indépendamment. Vous créez une table de données autonome en faisant glisser un <xref:System.Data.DataTable> de l’objet à partir de la **DataSet** onglet de la **boîte à outils** sur le **Concepteur de Dataset**.  
  
> [!NOTE]
>  Pour créer des tables de données par programmation, consultez [création d’un DataTable](http://msdn.microsoft.com/library/eecf9d78-60e3-4fdc-8de0-e56c13a89414).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datatable-with-tableadapter"></a>Création d’un DataTable avec un TableAdapter  
 Tables de données avec les TableAdapters incluent des méthodes que remplir la table de données et écrivent les modifications dans la base de données. Créer des TableAdapters en exécutant la **Assistant Configuration de TableAdapter** ou en faisant glisser des objets de base de données à partir de **Explorateur de serveurs** sur le **Concepteur de Dataset**.  
  
#### <a name="to-create-a-new-data-table-with-tableadapter"></a>Pour créer une nouvelle table de données avec un TableAdapter  
  
1.  Ouvrez votre jeu de données dans le **Concepteur de Dataset**. Pour plus d’informations, consultez [Comment : ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Faites glisser un **TableAdapter** à partir de la **DataSet** onglet de la **boîte à outils** sur le **Concepteur de Dataset**.  
  
     Le **Assistant Configuration de TableAdapter** s’ouvre.  
  
3.  Effectuez toutes les étapes de l'Assistant. Pour plus d’informations, consultez [Assistant Configuration de TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)  
  
#### <a name="to-create-a-new-data-table-with-a-tableadapter-from-server-explorer"></a>Pour créer une nouvelle table de données avec un TableAdapter à partir de l’Explorateur de serveurs  
  
1.  Ouvrez votre jeu de données dans le **Concepteur de Source de données**.  
  
2.  Faites glisser un objet de base de données (par exemple, une table) à partir de **Explorateur de serveurs** sur le **Concepteur de Dataset**.  
  
## <a name="creating-a-standalone-datatable"></a>Création d’un DataTable autonome  
 Les tables autonomes doivent avoir `Fill` logique implémentée afin d’être rempli avec des données. Pour plus d’informations sur le remplissage des tables de données autonome, consultez [remplissage d’un DataSet à partir d’un DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
#### <a name="to-create-a-new-stand-alone-data-table"></a>Pour créer une nouvelle table de données autonome  
  
1.  Ouvrez votre jeu de données dans le **Concepteur de Dataset**.  
  
2.  Faites glisser un <xref:System.Data.DataTable> à partir de la **DataSet** onglet de la **boîte à outils** sur le **Concepteur de Dataset**.  
  
3.  Ajouter des colonnes pour définir votre table de données. Pour plus d’informations, consultez [Comment : ajouter des colonnes à un DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataTable>   
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Procédure pas à pas : Affichage de données sur un formulaire Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)   
 [Fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Comment : établir une connexion à des données d’une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)