---
title: "Les instructions &#39;Get&#39; ne sont plus prises en charge (Visual Basic) | Microsoft Docs"
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
  - "vbc30767"
  - "bc30767"
helpviewer_keywords: 
  - "BC30767"
ms.assetid: 6aa62dcc-99aa-4051-a81e-3bbb6a8c355f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;Get&#39; ne sont plus prises en charge (Visual Basic)
Les instructions `Get` ne sont plus prises en charge. La fonctionnalité d’E\/S de fichier est normalement disponible dans l’espace de noms `Microsoft.VisualBasic`, mais la version ciblée de .NET Compact Framework ne la prend pas en charge.  
  
 **ID d’erreur :** BC30767  
  
### Pour corriger cette erreur  
  
-   Effectuez des opérations sur les fichiers avec les fonctions définies dans l’espace de noms <xref:System.IO>.  
  
## Voir aussi  
 <xref:System.IO>   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [File Access with Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)