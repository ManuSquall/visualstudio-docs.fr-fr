---
title: 'Comment : modifier des requêtes TableAdapter | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DbSource
- vbdata.Microsoft.VSDesigner.DataSource.DbSource
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- queries [Visual Basic], editing
- TableAdapters, editing queries
- data [Visual Studio], TableAdapters
- editing queries
ms.assetid: aac7b7b4-bd91-4225-95d4-a07643568c43
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 687336b979ef7e6d46ea6deb4a5682f3aec065be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287896"
---
# <a name="how-to-edit-tableadapter-queries"></a>Comment : modifier des requêtes TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous modifiez des requêtes TableAdapter avec le [modification des TableAdapters](../data-tools/editing-tableadapters.md) dans le **Concepteur de Dataset**. Vous devez modifier une requête TableAdapter lorsqu’il n’est plus le mieux aux besoins de votre application. (Vous pouvez également créer des requêtes supplémentaires sur le TableAdapter. Pour plus d’informations sur l’ajout de nouvelles requêtes, consultez [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).)  
  
> [!NOTE]
>  Si le [Assistant Configuration de TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) s’ouvre au lieu du **Assistant Configuration de requêtes TableAdapter**, vous avez peut-être sélectionné principale du TableAdapter `Fill` requête et non un le Requêtes supplémentaires du TableAdapter. Pour plus d’informations sur la modification du TableAdapter principales `Fill` de requête, consultez [Comment : modifier des TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
 ![TableAdapter avec plusieurs requêtes](../data-tools/media/tableadapter.gif "TableAdapter")  
  
### <a name="to-edit-a-tableadapter-query"></a>Pour modifier une requête TableAdapter  
  
1.  Ouvrez le jeu de données dans le **Concepteur de Dataset**. Pour plus d’informations, consultez [Comment : ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Sélectionnez la requête TableAdapter que vous souhaitez modifier.  
  
3.  Avec le bouton droit de la requête TableAdapter et sélectionnez **configurer**.  
  
     Le **Assistant Configuration de requêtes TableAdapter** s’ouvre, vous pouvez modifier la requête ou la procédure stockée pour cette requête.  
  
4.  Terminer la **Assistant Configuration de requêtes TableAdapter** avec les modifications que vous souhaitez. Pour plus d’informations, consultez [modification des TableAdapters](../data-tools/editing-tableadapters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [L’enregistrement des données](../data-tools/saving-data.md)   
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)