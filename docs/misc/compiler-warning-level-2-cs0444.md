---
title: "Avertissement du compilateur (niveau&#160;2) CS0444 | Microsoft Docs"
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
  - "CS0444"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0444"
ms.assetid: 5beb8c06-39d3-4b59-a7c3-5590200bd43d
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0444
Le type prédéfini 'type name 1' est introuvable dans 'System namespace 1' mais a été trouvé dans 'System namespace 2'  
  
 Aucun objet prédéfini, comme <xref:System.Int32>, n’a été trouvé à l’emplacement auquel le compilateur s’attendait à le trouver, mais il a été trouvé dans 'System namespace 2'.  
  
 L’erreur pourrait indiquer que le .NET Framework n’est pas correctement installé. Pour corriger cette erreur, réinstallez le .NET Framework.  
  
 Si vous écrivez vos propres bibliothèques de classes de base, vous pouvez également rencontrer cette erreur. Dans ce cas, pour corriger l’erreur, régénérez mscorlib.