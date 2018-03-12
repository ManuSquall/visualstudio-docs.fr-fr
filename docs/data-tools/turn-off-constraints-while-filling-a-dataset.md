---
title: "Désactiver les contraintes pendant le remplissage d’un jeu de données | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 88c8687511dd600802cc7c6ecdc12f0827fd7f6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Désactiver les contraintes pendant le remplissage d’un jeu de données
Si un jeu de données contient des contraintes (telles que les contraintes de clé étrangère), elles peuvent déclencher des erreurs liées à l’ordre des opérations qui sont exécutées sur le jeu de données. Par exemple, le chargement d’enregistrements enfants avant le chargement relatives aux enregistrements parents peuvent enfreindre une contrainte et provoque une erreur. Dès que vous chargez un enregistrement enfant, la contrainte vérifie l’enregistrement parent connexe et déclenche une erreur.  
  
 S’il n’existait aucun mécanisme permettant d’interrompre temporairement la contrainte, une erreur est générée chaque fois que vous avez essayé de charger un enregistrement dans la table enfant. Une autre consiste à interrompre toutes les contraintes dans un dataset avec le <xref:System.Data.DataRow.BeginEdit%2A>, et <xref:System.Data.DataRow.EndEdit%2A> propriétés.  
  
> [!NOTE]
>  Événements de validation (par exemple, <xref:System.Data.DataTable.ColumnChanging> et<xref:System.Data.DataTable.RowChanging>) ne seront pas déclenchés lorsque les contraintes sont désactivées.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Pour interrompre des contraintes de mise à jour par programme  
  
-   L’exemple suivant montre comment désactiver temporairement les contraintes vérification dans un jeu de données :  
  
     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Pour interrompre des contraintes de mise à jour à l’aide du Concepteur de Dataset  
  
1.  Ouvrez votre dataset dans le **Concepteur de Dataset**. Pour plus d’informations, consultez [procédure pas à pas : création d’un jeu de données dans le Concepteur de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Dans le **propriétés** , configurez la <xref:System.Data.DataSet.EnforceConstraints%2A> propriété `false`.  
  
## <a name="see-also"></a>Voir aussi  
 [Remplir des jeux de données à l’aide des TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Relations dans les datasets](../data-tools/relationships-in-datasets.md)