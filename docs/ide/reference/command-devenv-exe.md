---
title: "/Command (devenv.exe) | Microsoft Docs"
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
  - "/command (commutateur de Devenv)"
  - "Devenv, /command (commutateur)"
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Command (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Exécute la commande spécifiée après avoir lancé l'environnement de développement intégré \(IDE, Integrated Development Environment\) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Syntaxe  
  
```  
devenv /command CommandName  
```  
  
## Arguments  
 `CommandName`  
 Requis.  Nom complet d'une commande [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ou son alias, figurant entre guillemets doubles.  Pour plus d'informations sur la commande et Alias la syntaxe, consultez [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## Notes  
 Une fois le démarrage effectué, l'IDE exécute la commande nommée.  Si vous utilisez ce commutateur, l'IDE n'affiche pas la Page de démarrage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] au démarrage.  
  
 Si un complément expose une commande, vous pouvez utiliser ce commutateur pour lancer le complément à partir de la ligne de commande.  Pour plus d'informations, consultez [Comment : contrôler des compléments avec le Gestionnaire de compléments](../Topic/How%20to:%20Control%20Add-Ins%20By%20Using%20the%20Add-In%20Manager.md).  
  
## Exemple  
 Cet exemple lance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et exécute automatiquement la macro Open Favorite Files.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)