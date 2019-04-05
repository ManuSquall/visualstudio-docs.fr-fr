---
title: Essentials d’intégration de contrôle de source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b9189b647baa29d72975f84172696ecb54cd7f87
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952830"
---
# <a name="source-control-integration-essentials"></a>Éléments fondamentaux de l’intégration du contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prend en charge deux types d’intégration du contrôle de source : un plug-in de contrôle de code source qui fournit les fonctionnalités de base et est généré à l’aide de l’API de plug-in de contrôle de Source (anciennement appelé l’API MSSCCI) et une solution d’intégration de contrôle source hébergé sur le VSPackage qui Fournit des fonctionnalités plus robustes.  
  
## <a name="source-control-plug-in"></a>Plug-in de contrôle de code source  
 Un plug-in de contrôle de code Source est écrit en tant que DLL qui implémente l’API de plug-in de contrôle de Source. Fonctionnalité d’intégration de contrôle d’enregistrement et de la source est fournie via l’API. Cette approche est plus facile à implémenter qu’un VSPackage de contrôle de code source, et il utilise le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interface utilisateur (IU) pour la plupart des opérations de contrôle de code source.  
  
 Pour implémenter un plug-in à l’aide de l’API de plug-in de contrôle de Source de contrôle de code source, procédez comme suit :  
  
1. Créer une DLL qui implémente les fonctions spécifiées dans [Plug-ins de contrôle de code Source](../../extensibility/source-control-plug-ins.md).  
  
2. Inscrivez la DLL en rendant les entrées de Registre appropriée, comme décrit dans [Comment : Installer un plug-in de contrôle de code Source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3. Créer une application d’assistance de l’interface utilisateur et l’afficher lorsque vous y êtes invité par le Package de l’adaptateur de contrôle de code Source (le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] composant qui gère les fonctionnalités de contrôle de code source via le plug-ins de contrôle de code source).  
  
   Pour plus d’informations, consultez [création d’un plug-in de contrôle de Source](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>VSPackage de contrôle de code source  
 Un implémentation VSPackage de contrôle de code source vous permet de développer un remplacement personnalisé pour le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’interface utilisateur de contrôle de code source. Cette approche fournit un contrôle complet sur l’intégration du contrôle de code source, mais il vous oblige à fournir des éléments d’interface utilisateur et implémenter les interfaces de contrôle de code source qui seraient sinon fournies sous l’approche de plug-in.  
  
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
