---
title: "/UseEnv (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.UseEnvVars.ExcludePath"
  - "VC.Project.UseEnvVars.LibraryPath"
  - "VC.Project.UseEnvVars.SourcePath"
  - "VC.Project.UseEnvVars.Include"
  - "VC.Project.UseEnvVars.Path"
  - "VC.Project.UseEnvVars.ReferencePath"
helpviewer_keywords: 
  - "/UseEnv (commutateur de Devenv)"
  - "Devenv, /UseEnv"
  - "UseEnv (commutateur)"
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /UseEnv (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Démarre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et charge des variables d'environnement dans la boîte de dialogue **Répertoires de VC\+\+**.  
  
## Syntaxe  
  
```  
Devenv /useenv  
```  
  
## Exemple  
 L'exemple suivant démarre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et charge des variables d'environnement dans la boîte de dialogue **Répertoires VC\+\+**.  
  
```  
Devenv.exe /useenv  
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)