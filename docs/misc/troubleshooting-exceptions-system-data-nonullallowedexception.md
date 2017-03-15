---
title: "D&#233;pannage des exceptions&#160;: System.Data.NoNullAllowedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "NoNullAllowedException (classe)"
ms.assetid: 1ab87572-007f-4b84-bb13-c3626e7f89cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Data.NoNullAllowedException
Une exception <xref:System.Data.NoNullAllowedException> est levée lors d'une tentative d'insertion d'une valeur Null dans une colonne où <xref:System.Data.DataColumn.AllowDBNull%2A> a la valeur `false`.  
  
## Conseils associés  
 **Vérifiez que la valeur est DBNull avant de l'ajouter à la colonne.**  
 Si <xref:System.Data.DataColumn.AllowDBNull%2A> a la valeur `false`, il est impossible d'insérer la valeur Null. Pour plus d'informations, consultez <xref:System.DBNull>.  
  
 **Affectez à AllowDBNull la valeur true.**  
 Affecter la valeur `true` à cette propriété vous permet d'insérer des valeurs Null. Pour plus d'informations, consultez <xref:System.Data.DataColumn.AllowDBNull%2A>.  
  
## Notes  
 Si vous utilisez les boutons de navigation pour parcourir les enregistrements d'une table de base de données sur un formulaire de données, cette exception peut être levée avec les informations supplémentaires, "La colonne 'Colonne' n'autorise pas les valeurs null". Ce comportement se produit, car la clé primaire ou la colonne "NOT NULL" de la table de base de données n'a pas été sélectionnée dans l'Assistant Formulaire de données. Si la clé primaire ou la colonne "NOT NULL" de la base de données n'est pas sélectionnée dans l'Assistant Formulaire de données, lorsque vous créez le formulaire de données, l'option **Ajouter \- Crée un nouvel enregistrement** n'est pas désactivée. Pour contourner ce problème, sélectionnez les colonnes suivantes de la table sélectionnée lorsque vous ajoutez un formulaire de données à l'aide de l'Assistant Formulaire de données : la colonne principale et une colonne qui n'autorise pas les valeurs NULL.  
  
## Voir aussi  
 <xref:System.Data.NoNullAllowedException>   
 <xref:System.Data.DataRowCollection.Add%2A>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 <xref:System.Data.DataTable.LoadDataRow%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)