---
title: "&#39;&lt;sp&#233;cificateur&gt;&#39; n’est pas valide dans une d&#233;claration de variable membre | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30235"
  - "bc30235"
helpviewer_keywords: 
  - "BC30235"
ms.assetid: 8c5764e4-0096-4ca0-8656-05341a39833a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;sp&#233;cificateur&gt;&#39; n’est pas valide dans une d&#233;claration de variable membre
Une instruction `Dim` contient un mot clé non valide. Une instruction `Dim` peut inclure uniquement les mots clés `Friend`, `Private`, `Protected`, `Public`, `ReadOnly`, `Shadows`, `Shared` ou `Static`.  
  
 Ce message peut également s’afficher si vous déclarez une variable `Static` en dehors d’une procédure. Vous pouvez utiliser `Static` uniquement au niveau de la procédure.  
  
 Notez que si vous incluez un mot clé valide dans une instruction `Dim`, vous pouvez omettre le mot clé `Dim`.  
  
 **ID d’erreur :** BC30235  
  
### Pour corriger cette erreur  
  
1.  Supprimez le mot clé non valide de l’instruction `Dim`.  
  
2.  Si vous avez déclaré une variable `Static` en dehors d’une procédure, déplacez la déclaration à l’intérieur d’une procédure ou supprimez le mot clé `Static`.  
  
## Voir aussi  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)