---
title: "&#39;&lt;mot_cl&#233;&gt;&#39; n’est valide que dans une classe | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32002"
  - "vbc32002"
helpviewer_keywords: 
  - "BC32002"
ms.assetid: 773d8d50-abb8-4257-83a5-6e017c199d82
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;mot_cl&#233;&gt;&#39; n’est valide que dans une classe
Un mot clé associé aux classes, tel que `Me` ou `MyClass`, est utilisé en dehors d’une définition de classe.  
  
 **ID d’erreur :** BC32002  
  
### Pour corriger cette erreur  
  
-   Si le code qui utilise le mot clé implique des instances de classe, déplacez\-le vers une implémentation de classe.  
  
-   Si le code qui utilise le mot clé ne s’applique pas aux classes, supprimez le mot clé non valide.  
  
## Voir aussi  
 [Me](http://msdn.microsoft.com/fr-fr/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass \- supprimer](http://msdn.microsoft.com/fr-fr/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)