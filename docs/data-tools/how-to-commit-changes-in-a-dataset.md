---
title: "Comment&#160;: valider des modifications dans un groupe de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataSet.AcceptChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "groupes de données (Visual Basic), valider les modifications"
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: valider des modifications dans un groupe de donn&#233;es
Lorsque vous modifiez un groupe de données en mettant à jour, en insérant et en supprimant des enregistrements, le groupe de données conserve leurs versions d'origine et actuelles.  En outre, la propriété <xref:System.Data.DataRow.RowState%2A> de chaque ligne assure le suivi des enregistrements et vérifie s'ils sont dans leur état d'origine ou ont été mis à jour, insérés ou supprimés.  Ces informations sont particulièrement utiles lorsqu'il vous faut rechercher la version particulière d'une ligne.  En général, vous obtenez un sous\-ensemble de tous les enregistrements modifiés à envoyer à un autre processus.  Pour plus d'informations, consultez [Comment : récupérer des lignes modifiées](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  Après avoir traité toutes les lignes modifiées, vous pouvez valider les modifications en appelant la méthode `AcceptChanges` du <xref:System.Data.DataSet>, du <xref:System.Data.DataTable> ou du <xref:System.Data.DataRow>.  La méthode `AcceptChanges` est appelée automatiquement lors de l'appel aux méthodes de mise à jour d'un [TableAdapter](../data-tools/tableadapter-overview.md) ou d'un adaptateur de données.  Appelez `AcceptChanges` après avoir envoyé des modifications à une base de données.  
  
 Lorsque vous appelez <xref:System.Data.DataSet.AcceptChanges%2A> sur <xref:System.Data.DataSet>, tout objet <xref:System.Data.DataRow> qui est toujours en mode édition termine correctement ses modifications.  La propriété <xref:System.Data.DataRow.RowState%2A> de chaque <xref:System.Data.DataRow> change également ; les lignes <xref:System.Data.DataRowState> et <xref:System.Data.DataRowState> deviennent <xref:System.Data.DataRowState>, et les lignes <xref:System.Data.DataRowState> sont supprimées.  
  
 Si <xref:System.Data.DataSet> contient des objets <xref:System.Data.ForeignKeyConstraint>, l'appel à la méthode <xref:System.Data.DataSet.AcceptChanges%2A> entraîne également l'application de <xref:System.Data.AcceptRejectRule>.  
  
### Pour valider les modifications dans un groupe de données  
  
-   Appelez la méthode `AcceptChanges` sur un <xref:System.Data.DataSet>, un <xref:System.Data.DataTable> ou un <xref:System.Data.DataRow> pour valider les modifications apportées dans ces objets.  
  
     L'exemple suivant montre comment appeler la méthode `AcceptChanges` pour valider les modifications de la table `Customers`, après mise à jour d'une source de données :  
  
     [!CODE [VbRaddataEditing#11](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#11)]  
  
## Voir aussi  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Enregistrement des données](../data-tools/saving-data.md)   
 [Comment : récupérer des lignes modifiées](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)