---
title: "Services fournis (VSPackage du contr&#244;le de code Source) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services, packages de contrôle de code source"
  - "packages de contrôle de code source, services"
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Services fournis (VSPackage du contr&#244;le de code Source)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les services sont le mécanisme principal via lequel les fonctionnalités est partagée entre les VSPackages et entre l'environnement de développement intégré Visual \(IDE\) Studio et son VSPackages installé.  Pour une description détaillée des services et de leur importance dans l'IDE de Visual Studio, consultez[À l'aide et fournir des Services](../../extensibility/using-and-providing-services.md).  
  
## Le service de contrôle de code source  
 Visual Studio fournit deux couches de services, de services d'IDE\-niveau et de services de package.  L'IDE de Visual Studio fournit en mode natif les services d'IDE\-niveau.  le package de contrôle de code source consomme certains de ces services.  Le package de contrôle de code source comme un VSPackage partage sa fonctionnalité de contrôle de code source en fournissant un service de contrôle de code source privé de ses propres.  Le package de contrôle de code source encapsule le jeu d'interfaces contrôle\-mises en relation par source implémentées par est sous la forme de contrat pouvant être utilisé par l'IDE de Visual Studio.  
  
## Voir aussi  
 [Éléments de conception.](../../extensibility/internals/source-control-vspackage-design-elements.md)