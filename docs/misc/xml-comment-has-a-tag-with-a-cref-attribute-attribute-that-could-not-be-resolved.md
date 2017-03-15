---
title: "Le commentaire XML a une balise avec un attribut &#39;cref&#39; &#39;&lt;attribut&gt;&#39; qui n’a pas pu &#234;tre r&#233;solu | Microsoft Docs"
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
  - "bc42309"
  - "vbc42309"
helpviewer_keywords: 
  - "BC42309"
ms.assetid: c9f3cfa5-565f-48bf-8616-cfb25d24f89e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le commentaire XML a une balise avec un attribut &#39;cref&#39; &#39;&lt;attribut&gt;&#39; qui n’a pas pu &#234;tre r&#233;solu
Le commentaire XML a une balise avec un attribut 'cref' \<attribut\> qui n’a pas pu être résolu. Le commentaire XML sera ignoré.  
  
 Les balises peuvent avoir un attribut `cref` qui désigne un lien vers un autre élément du XML en spécifiant le nom relatif de l’identificateur. Au moment de la compilation, le compilateur remplace la valeur par l’identificateur XML qualifié pour la valeur pointée par l’utilisateur. Le compilateur utilise ses règles de résolution normales pour rechercher le type ou le membre.  
  
 **ID d’erreur :** BC42309  
  
### Pour corriger cette erreur  
  
-   Confirmez l’attribut `cref` de sorte qu’il pointe vers un élément de code valide.  
  
## Voir aussi  
 [How to: Create XML Documentation](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML Comment Tags](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)