---
title: "&#39;#End ExternalSource&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;#ExternalSource&#39; correspondant | Microsoft Docs"
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
  - "bc30578"
  - "vbc30578"
helpviewer_keywords: 
  - "BC30578"
ms.assetid: f011673d-eced-46a7-a08e-d54d86c8a76b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End ExternalSource&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;#ExternalSource&#39; correspondant
La directive `#ExternalSource` fait référence à du code externe, ce qui permet au compilateur de signaler précisément le moment où des exceptions se produisent dans ce code. Un bloc `#ExternalSource` doit commencer par `#ExternalSource` et se terminer par `#End ExternalSource`.  
  
 **ID d’erreur :** BC30578  
  
### Pour corriger cette erreur  
  
1.  Ajoutez `#ExternalSource` à l’emplacement approprié dans votre code.  
  
2.  Supprimez `#End ExternalSource` s’il est inutile.  
  
## Voir aussi  
 [\#ExternalSource Directive](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [NOTINBUILD Compilation conditionnelle \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)