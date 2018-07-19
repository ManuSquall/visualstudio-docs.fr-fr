---
title: Désactiver les contraintes pendant le remplissage d’un dataset
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d128216f84228c9cd4946f9a38c6c1b7845f92f1
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117236"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Désactiver les contraintes pendant le remplissage d’un dataset

Si un jeu de données contient des contraintes (telles que les contraintes de clé étrangère), ils peuvent déclencher des erreurs liées à l’ordre des opérations qui sont exécutées sur le jeu de données. Par exemple, le chargement des enregistrements enfants avant le chargement liés aux enregistrements parents peuvent violent une contrainte et provoquer une erreur. Dès que vous chargez un enregistrement enfant, la contrainte vérifie l’enregistrement parent connexes et génère une erreur.

S’il n’existait aucun mécanisme permettant d’interrompre temporairement la contrainte, une erreur est générée chaque fois que vous avez essayé de charger un enregistrement dans la table enfant. Une autre consiste à suspendre toutes les contraintes dans un dataset avec le <xref:System.Data.DataRow.BeginEdit%2A>, et <xref:System.Data.DataRow.EndEdit%2A> propriétés.

> [!NOTE]
> Événements de validation (par exemple, <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging>) n’est pas déclenché lorsque les contraintes sont désactivées.

## <a name="to-suspend-update-constraints-programmatically"></a>Pour interrompre des contraintes de mise à jour par programmation

-   L’exemple suivant montre comment désactiver temporairement la vérification dans un jeu de données des contraintes :

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Pour interrompre des contraintes de mise à jour à l’aide du Concepteur de Dataset

1.  Ouvrez votre jeu de données dans le **Concepteur de Dataset**. Pour plus d’informations, consultez [procédure pas à pas : création d’un jeu de données dans le Concepteur de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Dans le **propriétés** fenêtre, définissez la <xref:System.Data.DataSet.EnforceConstraints%2A> propriété `false`.

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relations dans les datasets](../data-tools/relationships-in-datasets.md)