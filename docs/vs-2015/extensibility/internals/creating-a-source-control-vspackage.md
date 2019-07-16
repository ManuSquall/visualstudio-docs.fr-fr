---
title: Création d’un VSPackage de contrôle de code Source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b1516cf358a4488ff02e650f6c703a1761a94a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196957"
---
# <a name="creating-a-source-control-vspackage"></a>Création d’un VSPackage de contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette documentation inclut des liens vers la vue d’ensemble de l’architecture d’un package de contrôle de code source intégré à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], l’API est définie par les interfaces à implémenter et les services à consommer et un exemple qui illustre une source simple contrôler l’implémentation du package.  
  
 Un VSPackage de contrôle de code source, vous pouvez créer un chemin d’accès de l’intégration approfondie pour le contrôle de code source à intégrer à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Il permet au package ignorer le contrôle de code source par défaut l’interface utilisateur hébergé par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], répondre aux demandes de contrôle de code source à partir du système de projet et d’interagir avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] des composants tels que **l’Explorateur de solutions**. Le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] met à votre disposition [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aux partenaires un mécanisme pour créer un VSPackage peut s’intégrer à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à l’aide d’un modèle de service.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Décrit le package de contrôle de code source, ce qui constitue une alternative plus avancée au plug-in pour l’implémentation des fonctionnalités de contrôle de code source dans le contrôle de code source [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Architecture](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Présente un diagramme et décrit les composants d’un package de contrôle de code source.  
  
 [Fonctionnalités](../../extensibility/internals/source-control-vspackage-features.md)  
 Décrit les différentes fonctionnalités d’un package de contrôle de code source.  
  
 [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Décrit la structure du VSPackage qu’un package de contrôle de code source doit implémenter pour l’intégration approfondie.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Explique comment créer un plug-in de contrôle de code source qui fournit les fonctionnalités de contrôle de code source dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interface utilisateur du contrôle source (IU).  
  
 [Contrôle de code source](../../extensibility/internals/source-control.md)  
 Décrit les options pour l’implémentation de contrôle de code source comme une fonctionnalité intégrée de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].
