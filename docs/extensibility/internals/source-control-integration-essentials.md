---
title: Notions fondamentales de l’intégration du contrôle de code source | Microsoft Docs
description: 'Découvrez les deux types d’intégration de contrôle de code source pris en charge par Visual Studio : un plug-in de contrôle de code source et une solution de contrôle de code source VSPackage.'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a4dd5186b20dfac4ad5a027e4519700ff8ac1f77
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876036"
---
# <a name="source-control-integration-essentials"></a>Éléments fondamentaux de l’intégration du contrôle de code source
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge deux types d’intégration du contrôle de code source : un plug-in de contrôle de code source qui fournit des fonctionnalités de base et est généré à l’aide de l’API de plug-in de contrôle de code source (anciennement appelée API MSSCCI) et une solution d’intégration de contrôle de code source basée sur VSPackage qui fournit des fonctionnalités plus robustes.

## <a name="source-control-plug-in"></a>Plug-in de contrôle de code source
 Un plug-in de contrôle de code source est écrit sous la forme d’une DLL qui implémente l’API de plug-in de contrôle de code source. L’inscription et la fonctionnalité d’intégration du contrôle de code source sont fournies par le biais de l’API. Cette approche est plus facile à implémenter qu’un VSPackage de contrôle de code source et utilise l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface utilisateur pour la plupart des opérations de contrôle de code source.

 Pour implémenter un plug-in de contrôle de code source à l’aide de l’API de plug-in de contrôle de code source, procédez comme suit :

1. Créez une DLL qui implémente les fonctions spécifiées dans les [plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md).

2. Inscrivez la DLL en effectuant les entrées de Registre appropriées, comme décrit dans [Comment : installer un plug-in de contrôle de code source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).

3. Créez une interface utilisateur d’assistance et affichez-la lorsque vous y êtes invité par le package de l’adaptateur de contrôle de code source (le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composant qui gère les fonctionnalités de contrôle de code source via les plug-ins de contrôle de code source).

   Pour plus d’informations, consultez [création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>VSPackage de contrôle de code source
 Une implémentation du VSPackage de contrôle de code source vous permet de développer un remplacement personnalisé pour l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface utilisateur du contrôle de code source. Cette approche fournit un contrôle complet sur l’intégration du contrôle de code source, mais elle vous oblige à fournir les éléments d’interface utilisateur et à implémenter les interfaces de contrôle de code source qui seraient autrement fournies sous l’approche de plug-in.

 Pour implémenter un VSPackage de contrôle de code source, vous devez :

1. Créez et inscrivez votre propre VSPackage de contrôle de code source, comme décrit dans [inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Remplacez l’interface utilisateur du contrôle de code source par défaut par votre interface utilisateur personnalisée. Voir [interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Spécifiez les glyphes à utiliser et gérez les événements de **Explorateur de solutions** glyphe. Consultez [contrôle Glyph](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Gérez les événements de modification de requête et d’enregistrement des requêtes, comme indiqué dans [requête modifier la requête enregistrer](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Pour plus d’informations, consultez [création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Voir aussi
- [Vue d'ensemble](../../extensibility/internals/source-control-integration-overview.md)
- [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)
