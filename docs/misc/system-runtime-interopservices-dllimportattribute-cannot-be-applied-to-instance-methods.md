---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; des m&#233;thodes d’instance | Microsoft Docs"
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
  - "vbc31529"
  - "bc31529"
helpviewer_keywords: 
  - "BC31529"
ms.assetid: c8bde5d7-c6bf-4d21-bb1a-e8627d65ad29
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; des m&#233;thodes d’instance
Une procédure non partagée est déclarée avec <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
 Le Common Language Runtime \(CLR\) reconnaît cet attribut et sa propriété <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> comme désignant une procédure de remplacement définie dans une bibliothèque de liens dynamiques \(DLL\) non gérée en dehors du .NET Framework. Quand le code appelle la procédure à laquelle <xref:System.Runtime.InteropServices.DllImportAttribute> est appliqué, le Common Language Runtime appelle plutôt la procédure non gérée désignée.  
  
 Étant donné que les plateformes non gérées qui sont en dehors du .NET Framework ne prennent pas en charge les procédures non partagées de la même manière que le .NET Framework, vous ne pouvez pas interagir avec elles en utilisant des procédures non partagées.  
  
 **ID d’erreur :** BC31529  
  
### Pour corriger cette erreur  
  
-   Si la procédure n’a pas besoin de s’appliquer individuellement à chaque instance de sa classe ou structure, déclarez\-la en tant que `Shared`.  
  
-   Si la procédure ne peut pas être `Shared`, supprimez <xref:System.Runtime.InteropServices.DllImportAttribute> de la déclaration de cette procédure.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)