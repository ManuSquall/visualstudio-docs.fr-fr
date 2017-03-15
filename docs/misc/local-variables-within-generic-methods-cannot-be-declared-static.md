---
title: "Les variables locales dans les m&#233;thodes g&#233;n&#233;riques ne peuvent pas &#234;tre d&#233;clar&#233;es &#39;Static&#39; | Microsoft Docs"
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
  - "vbc32068"
  - "bc32068"
helpviewer_keywords: 
  - "BC32068"
ms.assetid: cb5df484-76f9-4092-9d19-f26ddcf1c035
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les variables locales dans les m&#233;thodes g&#233;n&#233;riques ne peuvent pas &#234;tre d&#233;clar&#233;es &#39;Static&#39;
La déclaration d’une variable locale dans une procédure générique spécifie `Static`.  
  
 Actuellement, Visual Basic et le .NET Framework ne prennent pas en charge les combinaisons de variables statiques et de procédures génériques.  
  
 **ID d’erreur :** BC32068  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Static` de la déclaration de la variable.  
  
## Voir aussi  
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)   
 [NOTINBUILD Comment : allonger la durée de vie d’une variable](http://msdn.microsoft.com/fr-fr/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)