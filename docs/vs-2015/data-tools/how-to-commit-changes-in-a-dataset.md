---
title: 'Comment : valider des modifications dans un jeu de données | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataSet.AcceptChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], committing changes
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 40acd2a706ef7bc00ea1f90e51e90705be5658c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504121"
---
# <a name="how-to-commit-changes-in-a-dataset"></a>Comment : valider des modifications dans un groupe de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous apportez des modifications aux enregistrements dans un jeu de données par la mise à jour, insertion et suppression d’enregistrements, le jeu de données maintient les versions d’origine et actuelles des enregistrements. En outre, chaque ligne <xref:System.Data.DataRow.RowState%2A> propriété effectue le suivi de si les enregistrements sont dans leur état d’origine ou ont été mis à jour, insérées ou supprimées. Ces informations sont utiles lorsque vous devez rechercher une version particulière d’une ligne. En règle générale, vous obtenez un sous-ensemble de tous les enregistrements modifiés à envoyer à un autre processus. Pour plus d’informations, consultez [Comment : récupérer des lignes modifiées](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9). Une fois que vous avez traité toutes les lignes modifiées, vous pouvez valider les modifications en appelant le `AcceptChanges` méthode de la <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataRow>. Le `AcceptChanges` méthode est appelée automatiquement lorsque vous appelez les méthodes de mise à jour d’un [TableAdapter](../data-tools/tableadapter-overview.md) ou adaptateur de données. Appeler `AcceptChanges` après avoir soumis les modifications apportées à une base de données.  
  
 Lorsque vous appelez <xref:System.Data.DataSet.AcceptChanges%2A> sur le <xref:System.Data.DataSet>, n’importe quel <xref:System.Data.DataRow> objets toujours en mode édition termine correctement ses modifications. Le <xref:System.Data.DataRow.RowState%2A> propriété de chaque <xref:System.Data.DataRow> change également ; <xref:System.Data.DataRowState> et <xref:System.Data.DataRowState> lignes deviennent <xref:System.Data.DataRowState>, et <xref:System.Data.DataRowState> lignes sont supprimées.  
  
 Si le <xref:System.Data.DataSet> contient <xref:System.Data.ForeignKeyConstraint> objets, appelant le <xref:System.Data.DataSet.AcceptChanges%2A> méthode provoque également la <xref:System.Data.AcceptRejectRule> soient appliquées.  
  
### <a name="to-commit-changes-in-a-dataset"></a>Pour valider les modifications dans un jeu de données  
  
-   Appelez le `AcceptChanges` méthode soit un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataRow> pour valider les modifications dans ces objets.  
  
     L’exemple suivant montre comment appeler le `AcceptChanges` méthode pour valider les modifications dans le `Customers` table après la mise à jour une source de données :  
  
     [!code-csharp[VbRaddataEditing#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#11)]
     [!code-vb[VbRaddataEditing#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#11)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [L’enregistrement des données](../data-tools/saving-data.md)   
 [Comment : récupérer des lignes modifiées](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)