---
title: "Option /win32manifest ignor&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc2034"
  - "bc2034"
helpviewer_keywords: 
  - "BC2034"
ms.assetid: 8009553a-f6ba-4d2b-8ddd-8a9357bc928e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option /win32manifest ignor&#233;e
Option \/win32manifest ignorée. Elle ne peut être spécifiée que lorsque la cible est un assembly.  
  
 L’option de compilateur `/win32manifest` a été passée au compilateur Visual Basic alors que l’option `/target` est définie sur `module`.  
  
 **ID d’erreur :** BC2034  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’option de compilateur `/win32manifest` ou définissez l’option `/target` sur `exe`, `winexe` ou `library`.  
  
## Voir aussi  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/win32manifest](/dotnet/visual-basic/reference/command-line-compiler/win32manifest)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)