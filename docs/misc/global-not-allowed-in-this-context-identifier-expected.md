---
title: "&#39;Global&#39; n’est pas autoris&#233; dans ce contexte&#160;; identificateur attendu | Microsoft Docs"
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
  - "vbc36001"
  - "bc36001"
helpviewer_keywords: 
  - "BC36001"
ms.assetid: d515daa2-f53d-424c-81fd-e9c4b12f331b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Global&#39; n’est pas autoris&#233; dans ce contexte&#160;; identificateur attendu
Le mot clé `Global` est utilisé dans une instruction où il n’est pas autorisé.  
  
 Le mot clé `Global` permet d’accéder à un espace de noms défini en dehors de la hiérarchie d’espace de noms dans laquelle votre code doit être compilé.`Global` commence le chemin de qualification au niveau le plus extérieur de l’espace de noms de la bibliothèque de classes .NET Framework. Pour obtenir une illustration, consultez [Global \- delete](http://msdn.microsoft.com/fr-fr/18c8ba14-40f6-4978-8096-6a5852324635).  
  
 Certaines instructions, telles que `Imports` et `Namespace`, sont indépendantes de l’espace de noms dans lequel votre code doit être compilé. Elles nécessitent un chemin de qualification complet qui débute à l’espace de noms racine, comme <xref:System> ou <xref:Microsoft.VisualBasic>. Dans ces instructions, le mot clé `Global` est superflu et n’est pas autorisé.  
  
 **ID d’erreur :** BC36001  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Global` de l’instruction. Il n’est pas nécessaire.  
  
## Voir aussi  
 [Global \- delete](http://msdn.microsoft.com/fr-fr/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [Namespace Statement](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)