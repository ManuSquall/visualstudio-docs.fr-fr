---
title: "L’instruction &#39;#ExternalSource&#39; doit se terminer par un &#39;#End ExternalSource&#39; correspondant | Microsoft Docs"
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
  - "vbc30579"
  - "bc30579"
helpviewer_keywords: 
  - "BC30579"
ms.assetid: 8d658008-eddc-4b7d-a8d4-036da42957bf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction &#39;#ExternalSource&#39; doit se terminer par un &#39;#End ExternalSource&#39; correspondant
La directive `#ExternalSource` fait référence à du code externe, ce qui permet au compilateur de signaler précisément le moment où des exceptions se produisent dans ce code. Un bloc `#ExternalSource` doit commencer par `#ExternalSource` et se terminer par `#End ExternalSource`.  
  
 **ID d’erreur :** BC30579  
  
### Pour corriger cette erreur  
  
1.  Ajoutez `#End ExternalSource` à l’emplacement approprié dans votre code.  
  
2.  Supprimez le `#ExternalSource` initial s’il n’est pas nécessaire.  
  
## Voir aussi  
 [\#ExternalSource Directive](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [NOTINBUILD Compilation conditionnelle \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)