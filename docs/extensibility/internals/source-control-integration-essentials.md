---
title: Essentials d’intégration du contrôle de source | Documents Microsoft
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
ms.openlocfilehash: 0c3e93eb86fdc252f162331033207db5bdaa1569
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132032"
---
# <a name="source-control-integration-essentials"></a>Essentials de l’intégration de contrôle de code source
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge deux types d’intégration du contrôle de code source : un plug-in de contrôle de code source qui fournit les fonctionnalités de base et est construit à l’aide de l’API de plug-in de contrôle de Source (anciennement l’API MSSCCI) et une solution d’intégration de contrôle source basée sur le VSPackage qui Fournit des fonctionnalités plus robuste.  
  
## <a name="source-control-plug-in"></a>Plug-in de contrôle de code source  
 Un plug-in de contrôle de code Source est écrit en tant que DLL qui implémente l’API de plug-in de contrôle de Source. Fonctionnalité d’intégration de contrôle d’enregistrement et de la source est fournie via l’API. Cette approche est plus facile à implémenter qu’un VSPackage de contrôle de code source, et il utilise le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface utilisateur (IU) de la plupart des opérations de contrôle de code source.  
  
 Pour implémenter un plug-in à l’aide de l’API de plug-in de contrôle de Source de contrôle de code source, procédez comme suit :  
  
1.  Créer une DLL qui implémente les fonctions spécifiées dans [Plug-ins de contrôle de code Source](../../extensibility/source-control-plug-ins.md).  
  
2.  Inscrire la DLL en effectuant les entrées de Registre appropriées, comme décrit dans [Comment : installer un plug-in de contrôle de code Source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Créer un programme d’assistance de l’interface utilisateur et l’afficher lorsque vous y êtes invité par le Package de l’adaptateur de contrôle de Source (le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composant qui gère les fonctionnalités de contrôle de code source via le plug-ins de contrôle de code source).  
  
 Pour plus d’informations, consultez [création d’un plug-in de contrôle de code Source](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>VSPackage de contrôle de code source  
 Un implémentation d’un VSPackage de contrôle de code source vous permet de développer un remplacement personnalisé pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur de contrôle de code source. Cette approche fournit un contrôle complet sur l’intégration du contrôle de code source, mais vous devez fournir les éléments d’interface utilisateur et d’implémenter les interfaces de contrôle de code source qui sont sinon fournies sous l’approche de plug-in.  
  
 Pour implémenter un contrôle de code source VSPackage, vous devez :  
  
1.  Créer et inscrire votre propre contrôle de code source VSPackage, comme décrit dans [l’inscription et la sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Remplacez le contrôle de code source par défaut l’interface utilisateur de votre interface utilisateur personnalisée. Consultez [Interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Spécifiez les glyphes à utiliser et gérer **l’Explorateur de solutions** événements du glyphe. Consultez [glyphe contrôle](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Gérer les événements de requête modifier et enregistrer des requêtes, comme indiqué dans [requête modifier les requêtes enregistrer](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Pour plus d’informations, consultez [création d’un VSPackage de contrôle de Source](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble](../../extensibility/internals/source-control-integration-overview.md)   
 [Création d’un contrôle de Source de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)