---
title: "/SafeMode (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/SafeMode (commutateur de Devenv)"
  - "Devenv, /SafeMode (commutateur)"
  - "SafeMode (commutateur)"
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Démarre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en mode sans échec, chargeant uniquement l'environnement et les services par défaut.  
  
## Syntaxe  
  
```  
devenv /SafeMode   
```  
  
## Notes  
 Ce commutateur empêche le chargement de tous les VSPackages tiers au démarrage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], garantissant ainsi la stabilité de l'exécution.  
  
## Description  
 L'exemple suivant démarre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en mode sans échec.  
  
## Code  
  
```  
Devenv.exe /SafeMode  
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)