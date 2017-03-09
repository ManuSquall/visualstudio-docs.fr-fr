---
title: "Les litt&#233;raux XML et les propri&#233;t&#233;s d’axe XML ne sont pas disponibles pendant cette session de d&#233;bogage car ils ne sont pas utilis&#233;s dans cet assembly | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31196"
  - "bc31196"
helpviewer_keywords: 
  - "BC31196"
ms.assetid: 36be5c92-dd6b-41d4-894a-2bd71d772092
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les litt&#233;raux XML et les propri&#233;t&#233;s d’axe XML ne sont pas disponibles pendant cette session de d&#233;bogage car ils ne sont pas utilis&#233;s dans cet assembly
Un littéral XML ou une propriété d’axe XML ont été référencés dans la fenêtre **Espion** ou **Exécution** pendant une session de débogage dans laquelle le langage XML n’est pas disponible dans les fonctionnalités [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. C’est le cas pour un assembly qui n’utilise pas le langage XML dans les fonctionnalités [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou qui n’est pas une version Release.  
  
 **ID d’erreur :** BC31196  
  
### Pour corriger cette erreur  
  
-   Démarrez une nouvelle session de débogage à l’aide de la version Debug de l’assembly.  
  
## Voir aussi  
 [Debugging Your Visual Basic Application](/dotnet/visual-basic/developing-apps/debugging)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)