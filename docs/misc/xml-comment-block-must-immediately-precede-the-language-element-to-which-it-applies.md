---
title: "Le bloc de commentaires XML doit pr&#233;c&#233;der imm&#233;diatement l’&#233;l&#233;ment de langage auquel il se rapporte | Microsoft Docs"
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
  - "vbc42300"
  - "bc42300"
helpviewer_keywords: 
  - "BC42300"
ms.assetid: f9f7d1da-a723-4237-bd78-6db7ed8bc4aa
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le bloc de commentaires XML doit pr&#233;c&#233;der imm&#233;diatement l’&#233;l&#233;ment de langage auquel il se rapporte
Le bloc de commentaires XML doit précéder immédiatement l’élément de langage auquel il se rapporte. Le commentaire XML sera ignoré.  
  
 Cette erreur se produit également si une balise est mal placée ou formée de manière incorrecte.  
  
 **ID d’erreur :** BC42300  
  
### Pour corriger cette erreur  
  
1.  Déplacez le bloc de commentaires XML avant l’élément de langage auquel il se rapporte. Vérifiez qu’aucun caractère superflu n’a été inséré accidentellement avant la balise initiale.  
  
2.  Vérifiez que la balise est valide.  
  
## Voir aussi  
 [How to: Create XML Documentation](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML Comment Tags](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)