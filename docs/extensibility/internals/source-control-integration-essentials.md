---
title: Source Control Integration Essentials (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705240"
---
# <a name="source-control-integration-essentials"></a>Éléments fondamentaux de l’intégration du contrôle de code source
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]prend en charge deux types d’intégration de contrôle des sources : un plug-in de contrôle source qui fournit des fonctionnalités de base et est construit à l’aide de l’API plug-in de contrôle de source (anciennement connu sous le nom d’API MSSCCI), et une solution d’intégration de contrôle source basée sur VSPackage qui fournit des fonctionnalités plus robustes.

## <a name="source-control-plug-in"></a>Plug-in de contrôle des sources
 Un plug-in de contrôle des sources est écrit comme un DLL qui implémente l’API rechargeable de contrôle source. Les fonctionnalités d’enregistrement et d’intégration de contrôle des sources sont fournies par l’API. Cette approche est plus facile à implémenter qu’un contrôle source VSPackage, et elle utilise l’interface [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisateur (interface utilisateur) pour la plupart des opérations de contrôle des sources.

 Pour implémenter un plug-in de contrôle source à l’aide de l’API rechargeable source de contrôle, suivez ces étapes :

1. Créez un DLL qui implémente les fonctions spécifiées dans [les plug-ins source Control](../../extensibility/source-control-plug-ins.md).

2. Enregistrez le DLL en faisant les entrées de registre appropriées, comme décrit dans [Comment : Installer un plug-in de contrôle de source.](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. Créez une interface utilisateur d’aide et affichez-la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lorsqu’elle est incitée par le paquet d’adaptateur de contrôle des sources (le composant qui gère la fonctionnalité de contrôle des sources grâce à des plug-ins de contrôle source).

   Pour plus d’informations, voir [Créer un plug-in de contrôle source](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Contrôle des sources VSPackage
 Une implémentation VSPackage de contrôle source [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous permet de développer un remplacement personnalisé pour l’interface utilisateur de contrôle source. Cette approche assure un contrôle complet sur l’intégration du contrôle des sources, mais elle vous oblige à fournir les éléments d’interface utilisateur et à implémenter les interfaces de contrôle source qui, autrement, seraient fournies dans le cadre de l’approche de plug-in.

 Pour implémenter un contrôle source VSPackage, vous devez :

1. Créez et enregistrez votre propre contrôle source VSPackage, tel que décrit dans [l’enregistrement et la sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Remplacez l’interface utilisateur de contrôle par défaut par défaut par votre interface utilisateur personnalisée. Voir [l’interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Spécifier les glyphes à utiliser et gérer les événements de glyphe **solution Explorer.** Voir [Glyph Control](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Gérer requête Edit et Requête Enregistrer les événements, comme indiqué dans [Requête Edit Requête Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Pour plus d’informations, voir [Créer un contrôle source VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble](../../extensibility/internals/source-control-integration-overview.md)
- [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)
