---
title: "MSBuild Error MSB1027 | Microsoft Docs"
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
  - "MSBuild.CannotAutoDisableAutoResponseFile"
helpviewer_keywords: 
  - "MSB1027"
ms.assetid: 2ef8d643-616c-4608-be76-5c2c8e18a9e7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB1027
**Le commutateur \/noautoresponse ne peut pas être spécifié dans le fichier réponse automatique MSBuild.rsp, ni dans aucun autre fichier réponse référencé par le fichier réponse automatique.**  
  
 Le commutateur **\/noautoresponse** a été détecté dans le fichier MSBuild.rsp ou dans un autre fichier réponse inclus par le fichier MSBuild.rsp.  Le fichier réponse automatique ne peut pas être utilisé pour s'autodésactiver.  
  
### Pour corriger cette erreur  
  
-   Spécifiez un autre fichier réponse.  
  
-   Supprimez le commutateur **\/noautoresponse** du fichier réponse MSBuild.rsp.  
  
## Voir aussi  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)