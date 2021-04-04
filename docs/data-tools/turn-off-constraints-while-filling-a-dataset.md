---
title: Désactiver les contraintes pendant le remplissage d’un dataset
description: Savoir comment désactiver les contraintes pendant le remplissage d’un jeu de données. Suspendez les contraintes de mise à jour par programmation ou à l’aide de l’Concepteur de DataSet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 3280894ba1634f9775def74a88dcb413c94ba77a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215706"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Désactiver les contraintes pendant le remplissage d’un dataset

Si un DataSet contient des contraintes (telles que des contraintes de clé étrangère), il peut déclencher des erreurs liées à l’ordre des opérations effectuées sur le jeu de données. Par exemple, si vous chargez des enregistrements enfants avant de charger des enregistrements parents connexes, vous risquez de violer une contrainte et de générer une erreur. Dès que vous chargez un enregistrement enfant, la contrainte vérifie l’enregistrement parent associé et génère une erreur.

Si aucun mécanisme n’autorise l’interruption temporaire de contrainte, une erreur est déclenchée chaque fois que vous tentez de charger un enregistrement dans la table enfant. Une autre façon d’interrompre toutes les contraintes dans un DataSet est d’utiliser les <xref:System.Data.DataRow.BeginEdit%2A> Propriétés, et <xref:System.Data.DataRow.EndEdit%2A> .

> [!NOTE]
> Les événements de validation (par exemple <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> ) ne sont pas déclenchés lorsque les contraintes sont désactivées.

## <a name="to-suspend-update-constraints-programmatically"></a>Pour suspendre des contraintes Update par programmation

- L’exemple suivant montre comment désactiver temporairement la vérification des contraintes dans un jeu de données :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet10":::

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Pour suspendre les contraintes Update à l’aide de l’Concepteur de DataSet

1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [procédure pas à pas : création d’un DataSet dans le concepteur de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> sur `false`.

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relations dans les datasets](../data-tools/relationships-in-datasets.md)
