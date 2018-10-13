---
title: Désactiver les contraintes pendant le remplissage d’un jeu de données | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c47d3cb5e02117cb75ab86579b0cb3b166bd510
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259907"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Désactiver les contraintes pendant le remplissage d’un dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Si un jeu de données contient des contraintes (telles que les contraintes de clé étrangère), se déclenchent des erreurs liées à l’ordre des opérations qui sont exécutées sur le jeu de données. Par exemple, le chargement des enregistrements enfants avant les enregistrements parents de loadingrelated peut enfreindre une contrainte et provoque une erreur. Dès que vous chargez un enregistrement enfant, la contrainte vérifie l’enregistrement parent connexes et génère une erreur.  
  
 S’il n’existait aucun mécanisme permettant d’interrompre temporairement la contrainte, une erreur est générée chaque fois que vous avez essayé de charger un enregistrement dans la table enfant. Une autre consiste à suspendre toutes les contraintes dans un dataset avec le <xref:System.Data.DataRow.BeginEdit%2A>, et <xref:System.Data.DataRow.EndEdit%2A> propriétés.  
  
> [!NOTE]
>  Événements de validation (par exemple, <xref:System.Data.DataTable.ColumnChanging> et<xref:System.Data.DataTable.RowChanging>) n’est pas déclenché lorsque les contraintes sont désactivées.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Pour interrompre des contraintes de mise à jour par programmation  
  
-   L’exemple suivant montre comment désactiver temporairement la vérification dans un jeu de données des contraintes :  
  
     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Pour interrompre des contraintes de mise à jour à l’aide du Concepteur de Dataset  
  
1.  Ouvrez votre jeu de données dans le [création et modification de données typés](../data-tools/creating-and-editing-typed-datasets.md). Pour plus d’informations, consultez [Comment : ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> sur `false`.  
  
## <a name="see-also"></a>Voir aussi  
 [Remplir des jeux de données à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Relations dans les datasets](../data-tools/relationships-in-datasets.md)

