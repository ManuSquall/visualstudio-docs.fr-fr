---
title: "D&#233;pannage des exceptions&#160;: System.ArgumentOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
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
  - "ArgumentOutOfRangeException (classe)"
ms.assetid: f53c58d9-7c4e-407f-93d3-1e59d90d98f5
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.ArgumentOutOfRangeException
Une <xref:System.ArgumentOutOfRangeException> est levée lorsqu'une méthode est appelée et qu'au moins un des arguments passés à la méthode n'est pas une référence null \(`Nothing` en Visual Basic\) et ne contient pas de valeur valide.  
  
## Conseils associés  
 **Assurez\-vous que tous les arguments pour cette méthode ont des valeurs valides, telles que définies par la méthode appelée.**  
 Les arguments qui ne sont pas des références null doivent contenir des valeurs valides.  
  
 **Si vous utilisez une collection, assurez\-vous que la taille de l'index est inférieure à celle de la collection.**  
 L'index doit se situer dans la plage de taille de la collection et ne peut pas dépasser la plage de taille ou être inférieur à zéro. Pour plus d'informations, consultez [Collections](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md).  
  
 **Lorsque vous utilisez les méthodes FindString ou FindExactString surchargées à deux arguments de la classe ComboBox or ListBox, vérifiez le paramètre startIndex.**.  
 Cette exception peut être levée si `startIndex` est égal à la valeur d'index du dernier élément de la liste associée. Pour la contourner, passez 0 comme valeur du paramètre `startIndex` ou utilisez la méthode à un argument `FindString` ou `FindStringExact`. Pour plus d'informations, consultez [CComboBox::FindString](../Topic/CComboBox::FindString.md) ou [CListBox::FindString](../Topic/CListBox::FindString.md).  
  
## Voir aussi  
 <xref:System.ArgumentOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)