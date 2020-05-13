---
title: Création d’un VSPackage source Control (fr) Microsoft Docs
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
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709188"
---
# <a name="create-a-source-control-vspackage"></a>Créer un contrôle source VSPackage
Cette documentation comprend des liens vers l’aperçu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de l’architecture d’un paquet de contrôle des sources intégré à , l’API qui est défini par les interfaces à implémenter et les services à consommer, et un échantillon qui illustre une simple mise en œuvre de l’ensemble de contrôle des sources.

 Avec un contrôle source VSPackage, vous pouvez créer un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]chemin d’intégration profonde pour le contrôle des sources à intégrer avec . Il permet au paquet de contourner l’interface [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilisateur de contrôle source par défaut hébergée par, répondre aux demandes de contrôle des sources du système de projet, et d’interagir avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des composants tels que Solution **Explorer**. Les [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partenaires habilitent avec un mécanisme pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] créer un VSPackage qui peut s’intégrer à l’aide d’un modèle de service.

## <a name="in-this-section"></a>Contenu de cette section
- [Bien démarrer](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Discute du paquet de contrôle source, qui est une alternative plus avancée au [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]plug-in de contrôle source pour la mise en œuvre des fonctionnalités de contrôle des sources dans .

- [Architecture](../../extensibility/internals/source-control-vspackage-architecture.md)

 Présente un diagramme et explique les composants d’un paquet de contrôle des sources.

- [Fonctionnalités](../../extensibility/internals/source-control-vspackage-features.md)

 Décrit les différentes caractéristiques d’un ensemble de contrôle source.

- [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Décrit la structure de l’emballage VS qu’un paquet de contrôle source doit mettre en œuvre pour une intégration profonde.

## <a name="related-sections"></a>Sections connexes
- [Créer un plug-in de contrôle source](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Discute de la façon de créer un plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de contrôle source qui fournit la fonctionnalité de contrôle des sources dans l’interface utilisateur de contrôle source (interface utilisateur de contrôle de source ).

- [Contrôle de code source](../../extensibility/internals/source-control.md)

 Discute des options pour mettre en œuvre le contrôle des sources comme une caractéristique intégrée de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
