---
title: "/Log (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Log (commutateur de Devenv)"
  - "Devenv, /Log (commutateur)"
  - "Log (commutateur) (devenv.exe)"
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Log (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Enregistre toute l'activité dans le fichier journal de résolution des problèmes.  Ce fichier apparaît une fois que vous avez appelé `devenv /log` au moins une fois.  Par défaut, le fichier journal est :  
  
 *%APPDATA%*\\Microsoft\\VisualStudio\\*Version*\\ActivityLog.xml  
  
 où *Version* est la version de Visual Studio.  Toutefois, vous pouvez spécifier un autre chemin d'accès et\/ou nom de fichier.  
  
## Syntaxe  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## Notes  
 Ce commutateur doit apparaître à la fin de la ligne de commande, après tous les autres commutateurs.  
  
 Le journal est rédigé pour toutes les instances de Visual Studio que vous avez appelées avec le commutateur \/log.  Il ne consigne pas les instances de Visual Studio que vous avez appelées sans ce commutateur.  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)