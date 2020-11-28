---
title: Création d’un VSPackage de contrôle de code source | Microsoft Docs
description: Découvrez comment créer un VSPackage de contrôle de code source qui crée un chemin d’intégration profond pour le contrôle de code source à intégrer à Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69e526cea292544c725abc7ffb54d0b29ad88403
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305580"
---
# <a name="create-a-source-control-vspackage"></a>Créer un VSPackage de contrôle de code source
Cette documentation contient des liens vers la vue d’ensemble de l’architecture d’un package de contrôle de code source intégré à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , l’API définie par les interfaces à implémenter et les services à consommer, ainsi qu’un exemple qui illustre une implémentation de package de contrôle de code source simple.

 Avec un VSPackage de contrôle de code source, vous pouvez créer un chemin d’intégration profond pour l’intégration du contrôle de code source à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Elle permet au package de contourner l’interface utilisateur du contrôle de code source par défaut hébergée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , de répondre aux demandes de contrôle de code source du système de projet et d’interagir avec des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composants tels que **Explorateur de solutions**. Le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] permet aux [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partenaires de créer un VSPackage qui peut s’intégrer à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’aide d’un modèle de service.

## <a name="in-this-section"></a>Dans cette section
- [Prise en main](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Décrit le package de contrôle de code source, qui est une alternative plus avancée au plug-in de contrôle de code source pour l’implémentation des fonctionnalités de contrôle de code source dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Architecture](../../extensibility/internals/source-control-vspackage-architecture.md)

 Présente un diagramme et décrit les composants d’un package de contrôle de code source.

- [Caractéristiques](../../extensibility/internals/source-control-vspackage-features.md)

 Décrit les différentes fonctionnalités d’un package de contrôle de code source.

- [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Décrit la structure du VSPackage qu’un package de contrôle de code source doit implémenter pour une intégration profonde.

## <a name="related-sections"></a>Sections connexes
- [Créer un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Explique comment créer un plug-in de contrôle de code source qui fournit des fonctionnalités de contrôle de code source dans l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface utilisateur du contrôle de code source.

- [Contrôle de code source](../../extensibility/internals/source-control.md)

 Décrit les options permettant d’implémenter le contrôle de code source en tant que fonctionnalité intégrée de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
