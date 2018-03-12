---
title: "Création d’un VSPackage de contrôle Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c3fac86583126e94bcfaea65a82c7cf923275769
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-source-control-vspackage"></a>Création d’un VSPackage de contrôle de code Source
Cette documentation inclut des liens vers la vue d’ensemble de l’architecture d’un package de contrôle de code source intégré à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l’API est définie par les interfaces à implémenter et les services à consommer et un exemple qui illustre une source simple contrôler l’implémentation du package.  
  
 Avec un contrôle de code source VSPackage, vous pouvez créer un chemin d’accès de l’intégration en profondeur pour le contrôle de code source à intégrer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Il permet au package d’ignorer le contrôle de code source par défaut l’interface utilisateur hébergée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], répondre aux demandes de contrôle de code source à partir du système de projet et d’interagir avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composants tels que **l’Explorateur de solutions**. Le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Responsabilise [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avec un mécanisme pour créer un VSPackage qui peut s’intégrer avec des partenaires [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à l’aide d’un modèle de service.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Décrit le package de contrôle de source, qui est une alternative plus avancée au plug-in pour l’implémentation des fonctionnalités de contrôle de code source dans le contrôle de code source [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Architecture](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Présente un diagramme et décrit les composants d’un package de contrôle de code source.  
  
 [Fonctionnalités](../../extensibility/internals/source-control-vspackage-features.md)  
 Décrit les différentes fonctionnalités d’un package de contrôle de code source.  
  
 [Éléments de conception.](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Décrit la structure du VSPackage qu’un package de contrôle de code source doit implémenter pour l’intégration en profondeur.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Explique comment créer un plug-in de contrôle de code source qui fournit les fonctionnalités de contrôle de code source dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface utilisateur du contrôle source (IU).  
  
 [Contrôle de code source](../../extensibility/internals/source-control.md)  
 Décrit les options pour l’implémentation du contrôle de code source en tant qu’une fonctionnalité intégrée de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].