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
ms.workload:
- data-storage
ms.openlocfilehash: aaf566c211cd79657b67a5af72d53c718cd2507a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951457"
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

1.  Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un jeu de données dans le Concepteur de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> sur `false`.

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relations dans les datasets](../data-tools/relationships-in-datasets.md)