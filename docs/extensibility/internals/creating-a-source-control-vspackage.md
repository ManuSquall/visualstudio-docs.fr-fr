---
title: "Cr&#233;ation d&#39;un VSPackage de contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de code source (Visual Studio SDK), la création de packages de contrôle de code source"
  - "packages de contrôle de code source"
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Cr&#233;ation d&#39;un VSPackage de contr&#244;le de code Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette documentation inclut des liens vers la vue d'ensemble de l'architecture d'un package de contrôle de code source intégré à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'API qui est définie par les interfaces à implémenter et les services à consommer, et un exemple qui montre une implémentation simple de package de contrôle de code source.  
  
 Avec un contrôle de code source VSPackage, vous pouvez créer un chemin d'accès complet d'intégration du contrôle de code source s'intègre à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Il permet au package pour ignorer le contrôle de code source par défaut interface utilisateur hébergé par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], pour répondre aux demandes de contrôle de code source du système de projet, et interagir avec des composants de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tels qu' **Explorateur de solutions**.  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] autorise les partenaires de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avec un mécanisme pour créer un VSPackage qui peut s'intégrer à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à l'aide d'un modèle de service.  
  
## Dans cette section  
 [Prise en main](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Décrit le package de contrôle de code source, qui est une alternative plus avancée au plug\-in contrôle de code source pour implémenter des fonctionnalités de contrôle de code source dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Architecture](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Présente un diagramme et décrit les composants d'un package de contrôle de code source.  
  
 [Fonctionnalités](../../extensibility/internals/source-control-vspackage-features.md)  
 décrit les différentes fonctionnalités d'un package de contrôle de code source.  
  
 [Éléments de conception.](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Décrit la structure de VSPackage qu'un package de contrôle de code source doit implémenter pour l'intégration profonde.  
  
## Rubriques connexes  
 [Création d'un contrôle de Source de plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Explique comment créer un plug\-in contrôle de code source qui fournit la fonctionnalité de contrôle de code source dans l'interface utilisateur du contrôle de code source de \(UI\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
 [Contrôle de code source](../../extensibility/internals/source-control.md)  
 Traite des options pour l'implémentation du contrôle de code source comme une fonctionnalité intégrée de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].