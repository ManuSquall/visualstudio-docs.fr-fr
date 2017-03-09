---
title: "Erreur du compilateur CS0721 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0721"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0721"
ms.assetid: 7ab8591d-df8a-440c-80d6-61b438a935fd
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0721
'type' : les types static ne peuvent pas être utilisés en tant que paramètres  
  
 Un type static ne peut pas être utilisé comme un paramètre. Puisqu’aucune instance de type static ne peut être créée, aucune instance ne pourra être passée en tant que paramètre.  
  
 L’exemple suivant génère l’erreur CS0721 :  
  
```  
// CS0721.cs public static class SC { } public class CMain { public void F(SC sc)  // CS0721 { } public static void Main() { } }  
```