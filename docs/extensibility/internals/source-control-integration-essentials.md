---
title: Essentials d’intégration de contrôle de source | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4533cac0ba6cbbcf5cf4354afdb29eefc5b2b726
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879166"
---
# <a name="source-control-integration-essentials"></a>Éléments fondamentaux de l’intégration du contrôle de code source
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge deux types d’intégration du contrôle de source : un plug-in de contrôle de code source qui fournit les fonctionnalités de base et est généré à l’aide de l’API de plug-in de contrôle de Source (anciennement appelé l’API MSSCCI) et une solution d’intégration de contrôle source hébergé sur le VSPackage qui Fournit des fonctionnalités plus robustes.  
  
## <a name="source-control-plug-in"></a>Plug-in de contrôle de code source  
 Un plug-in de contrôle de code Source est écrit en tant que DLL qui implémente l’API de plug-in de contrôle de Source. Fonctionnalité d’intégration de contrôle d’enregistrement et de la source est fournie via l’API. Cette approche est plus facile à implémenter qu’un VSPackage de contrôle de code source, et il utilise le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface utilisateur (IU) pour la plupart des opérations de contrôle de code source.  
  
 Pour implémenter un plug-in à l’aide de l’API de plug-in de contrôle de Source de contrôle de code source, procédez comme suit :  
  
1. Créer une DLL qui implémente les fonctions spécifiées dans [Plug-ins de contrôle de code Source](../../extensibility/source-control-plug-ins.md).  
  
2. Inscrivez la DLL en rendant les entrées de Registre appropriée, comme décrit dans [Comment : installer un plug-in de contrôle de Source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3. Créer une application d’assistance de l’interface utilisateur et l’afficher lorsque vous y êtes invité par le Package de l’adaptateur de contrôle de code Source (le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composant qui gère les fonctionnalités de contrôle de code source via le plug-ins de contrôle de code source).  
  
   Pour plus d’informations, consultez [création d’un plug-in de contrôle de Source](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>VSPackage de contrôle de code source  
 Un implémentation VSPackage de contrôle de code source vous permet de développer un remplacement personnalisé pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur de contrôle de code source. Cette approche fournit un contrôle complet sur l’intégration du contrôle de code source, mais il vous oblige à fournir des éléments d’interface utilisateur et implémenter les interfaces de contrôle de code source qui seraient sinon fournies sous l’approche de plug-in.  
  
 Pour implémenter un VSPackage de contrôle de code source, vous devez :  
  
1. Créer et inscrire votre propre contrôle de code source VSPackage, comme décrit dans [inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2. Remplacez le contrôle de code source par défaut l’interface utilisateur avec votre interface utilisateur personnalisée. Consultez [Interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3. Spécifiez des glyphes à utiliser et gérer **l’Explorateur de solutions** événements de glyphe. Consultez [contrôle de glyphe](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4. Gère les événements de modification de la requête et d’enregistrement des requêtes, comme indiqué dans [requête d’enregistrement des requêtes modifier](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
   Pour plus d’informations, consultez [création d’un VSPackage de contrôle de code Source](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble](../../extensibility/internals/source-control-integration-overview.md)   
 [Création d’un contrôle de Source de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)