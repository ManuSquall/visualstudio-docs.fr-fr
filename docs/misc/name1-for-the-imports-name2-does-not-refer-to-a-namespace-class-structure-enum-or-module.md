---
title: "&#39;&lt;nom1&gt;&#39; pour les Imports &#39;&lt;nom2&gt;&#39; ne fait pas r&#233;f&#233;rence &#224; un Namespace, Class, Structure, Enum ou Module | Microsoft Docs"
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
  - "vbc30467"
  - "bc30467"
helpviewer_keywords: 
  - "BC30467"
ms.assetid: a4b8a23b-ba1b-44f7-9584-258dd2607581
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom1&gt;&#39; pour les Imports &#39;&lt;nom2&gt;&#39; ne fait pas r&#233;f&#233;rence &#224; un Namespace, Class, Structure, Enum ou Module
Vous avez tenté d’utiliser l’instruction `Imports` sur un élément qui ne correspond à aucun des éléments suivants: `Namespace`, `Class`, `Structure`, `Enum` et `Module`. L’instruction `Imports` importe des noms d’espaces de noms à partir de projets et d’assemblys référencés, ou des noms d’espaces de noms définis dans le même projet que le module dans lequel elle apparaît.  
  
 **ID d’erreur :** BC30467  
  
### Pour corriger cette erreur  
  
-   Vérifiez l’entité que vous essayez d’importer et assurez\-vous qu’elle peut être utilisée avec une instruction `Imports`.  
  
## Voir aussi  
 [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)