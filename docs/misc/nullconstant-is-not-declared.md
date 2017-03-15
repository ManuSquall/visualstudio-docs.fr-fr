---
title: "&#39;&lt;constante_null&gt;&#39; n’est pas d&#233;clar&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30822"
  - "vbc30822"
helpviewer_keywords: 
  - "BC30822"
ms.assetid: dda0e2c1-46a3-4cc4-b36c-0858a5259bac
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;constante_null&gt;&#39; n’est pas d&#233;clar&#233;
'\<constante\_null\>' n’est pas déclaré. La constante 'Null' n’est plus prise en charge ; utilisez 'System.DBNull' à la place.  
  
 Une instruction utilise le mot clé `Null` qui n’est plus pris en charge par Visual Basic.  
  
 **ID d’erreur :** BC30822  
  
### Pour corriger cette erreur  
  
1.  Utilisez <xref:System.DBNull> à la place de `Null`. Cela est illustré par l'exemple suivant.  
  
    ```  
    Sub TestDBNull() Dim t As DataTable ' Assume the DataGrid is bound to a DataTable. t = CType(DataGrid1.DataSource, DataTable) Dim r As DataRow r = t.Rows(datagrid1.CurrentCell.RowNumber) r.BeginEdit r(1) = System.DBNull.Value ' Assign DBNull to the record. r.EndEdit r.AcceptChanges If r.IsNull(1) Then MsgBox("") End If End Sub  
    ```  
  
2.  Utilisez le mot clé [Nothing](/dotnet/visual-basic/language-reference/nothing) pour les assignations et les comparaisons quand vous utilisez des variables d’objet. Cela est illustré par l'exemple suivant.  
  
    ```  
    Sub TestNothing() Dim cls As Object ' cls is Nothing if it has not been assigned using the New keyword. If (cls Is Nothing) Then MsgBox("cls is Nothing") End If cls = Nothing ' Assign Nothing to the class variable cls. End Sub  
    ```  
  
## Voir aussi  
 <xref:System.DBNull>   
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/fr-fr/0483590a-6309-449c-a2fa-effa26a03b95)