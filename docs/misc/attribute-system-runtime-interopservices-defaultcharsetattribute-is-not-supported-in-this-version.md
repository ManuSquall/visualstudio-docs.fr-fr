---
title: "L’attribut &#39;System.Runtime.InteropServices.DefaultCharSetAttribute&#39; n’est pas pris en charge dans cette version | Microsoft Docs"
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
  - "bc32510"
  - "vbc32510"
helpviewer_keywords: 
  - "BC32510"
ms.assetid: e2eec233-6e0b-4f2f-a801-b0274e579c0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’attribut &#39;System.Runtime.InteropServices.DefaultCharSetAttribute&#39; n’est pas pris en charge dans cette version
L’attribut <xref:System.Runtime.InteropServices.DefaultCharSetAttribute?displayProperty=fullName> permet de spécifier le jeu de caractères à utiliser dans les chaînes marshalées. Sa valeur accepte un membre de l’énumération <xref:System.Runtime.InteropServices.CharSet?displayProperty=fullName>.  
  
 La version actuelle de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne prend pas en charge cet attribut. Une prise en charge est possible dans les futures versions.  
  
 **ID d’erreur :** BC32510  
  
### Pour corriger cette erreur  
  
-   Utilisez chaque [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement) afin de spécifier le jeu de caractères pour la procédure externe qu’elle déclare. L'exemple suivant illustre ce comportement.  
  
    ```  
    Ansi Declare Function GetUserName Lib "advapi32.dll" _ (ByVal lpBuffer As String, ByRef nSize As Integer) As Integer Unicode Declare Sub externalProc Lib "projectlib.dll" _ (ByVal arg As Double)  
    ```  
  
     Si vous ne spécifiez pas de jeu de caractères dans l’instruction `Declare`, la valeur par défaut sera ANSI.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute>   
 <xref:System.Runtime.InteropServices.CharSet>   
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)