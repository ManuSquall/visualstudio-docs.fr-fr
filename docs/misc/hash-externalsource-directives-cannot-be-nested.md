---
title: "Les directives &#39;#ExternalSource&#39; ne peuvent pas &#234;tre imbriqu&#233;es | Microsoft Docs"
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
  - "bc30580"
  - "vbc30580"
helpviewer_keywords: 
  - "BC30580"
ms.assetid: 56c6ef4b-28b1-4a62-8afa-d83a7742b507
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les directives &#39;#ExternalSource&#39; ne peuvent pas &#234;tre imbriqu&#233;es
Vous avez tenté de placer une directive `#ExternalSource` dans un autre bloc `#ExternalSource`. La directive `#ExternalSource` fait référence à du code externe, ce qui permet au compilateur de signaler précisément le moment où des exceptions se produisent dans ce code.  
  
 Les blocs `#ExternalSource` ne peuvent pas être imbriqués dans d’autres blocs `#ExternalSource`.  
  
 **ID d’erreur :** BC30580  
  
### Pour corriger cette erreur  
  
-   Déplacez la directive `#ExternalSource` interne en dehors du bloc `#ExternalSource` englobant.  
  
## Voir aussi  
 [\#ExternalSource Directive](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [NOTINBUILD Compilation conditionnelle \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)