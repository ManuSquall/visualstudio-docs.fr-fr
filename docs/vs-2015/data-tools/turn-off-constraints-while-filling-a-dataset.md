---
title: Désactiver les contraintes pendant le remplissage d’un jeu de données | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6646f669bf2c465d8e0f705f8fba956b979952ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667169"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Désactiver les contraintes pendant le remplissage d’un dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si un DataSet contient des contraintes (telles que des contraintes de clé étrangère), Theycan déclenche des erreurs liées à l’ordre des opérations effectuées sur le jeu de données. Par exemple, le chargement des enregistrements enfants avant les enregistrements parents loadingrelated peut violer une contrainte et générer une erreur. Dès que vous chargez un enregistrement enfant, la contrainte vérifie l’enregistrement parent associé et génère une erreur.

 Si aucun mécanisme n’autorise l’interruption temporaire de contrainte, une erreur est déclenchée chaque fois que vous tentez de charger un enregistrement dans la table enfant. Une autre façon d’interrompre toutes les contraintes dans un jeu de données consiste à utiliser les propriétés <xref:System.Data.DataRow.BeginEdit%2A> et <xref:System.Data.DataRow.EndEdit%2A>.

> [!NOTE]
> Les événements de validation (par exemple, <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging>) ne sont pas déclenchés lorsque les contraintes sont désactivées.

### <a name="to-suspend-update-constraints-programmatically"></a>Pour suspendre des contraintes Update par programmation

- L’exemple suivant montre comment désactiver temporairement la vérification des contraintes dans un jeu de données :

     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]

### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Pour suspendre les contraintes Update à l’aide de l’Concepteur de DataSet

1. Ouvrez votre jeu de données dans le Concepteur de DataSet. Pour plus d’informations, consultez [Comment : ouvrir un DataSet dans le concepteur de DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> sur `false`.

## <a name="see-also"></a>Voir aussi
 [Remplir des jeux de données à l’aide](../data-tools/fill-datasets-by-using-tableadapters.md) [de relations de TableAdapters dans les jeux de données](../data-tools/relationships-in-datasets.md)
