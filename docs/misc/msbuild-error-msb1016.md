---
title: "MSBuild Error MSB1016 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.MissingVerbosityError"
helpviewer_keywords: 
  - "MSB1016"
ms.assetid: 967a9757-0513-48ae-bf1d-b1b019993c70
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB1016
**Spécifiez le niveau de commentaires.**  
  
 Un niveau de commentaires doit être spécifié pour le commutateur **\/verbosity**.  
  
### Pour corriger cette erreur  
  
1.  Spécifiez le niveau de commentaires à l'aide du format `/verbosity:<level>`.  Les niveaux de commentaires disponibles sont : q\[uiet\], m\[inimal\], n\[ormal\], d\[etailed\], et diag\[nostic\], par exemple, `/verbosity:quiet`, `/verbosity:q` ou  `/v:q`  
  
## Voir aussi  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)