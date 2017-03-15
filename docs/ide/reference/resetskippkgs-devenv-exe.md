---
title: "/ResetSkipPkgs (devenv.exe) | Microsoft Docs"
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
  - "/ResetSkipPkgs (commutateur de Devenv)"
  - "Devenv, /ResetSkipPkgs (commutateur)"
  - "ResetSkipPkgs (commutateur)"
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Efface toutes les options pour ignorer le chargement ajouté à VSPackages par les utilisateurs qui souhaitent éviter de charger les VSPackages à problème, puis démarre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Syntaxe  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## Notes  
 La présence d'une balise SkipLoading désactive le chargement d'un package VS. Effacer la balise réactive le chargement du package VS.  
  
## Exemple  
 L'exemple suivant efface toutes les balises SkipLoading.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)