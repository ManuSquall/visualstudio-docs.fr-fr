---
title: Création d’un plug-in de contrôle de code source | Microsoft Docs
description: Découvrez comment créer un plug-in de contrôle de code source qui ajoute une fonctionnalité de contrôle de code source à l’environnement de développement intégré (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ae887e8752e1603af173ed569d19a6602ac84f0
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305365"
---
# <a name="create-a-source-control-plug-in"></a>Créer un plug-in de contrôle de code source
Le kit de développement logiciel (SDK) Visual Studio fournit des ressources qui vous permettent d’ajouter des fonctionnalités de contrôle de code source à l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE). Elle vous permet d’utiliser n’importe quelle DLL de plug-in conforme à l’API de plug-in de contrôle de code source décrite dans cette documentation.

## <a name="in-this-section"></a>Dans cette section
- [Prise en main](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Décrit comment installer un plug-in de contrôle de code source et met en surbrillance les versions d’API de plug-in de contrôle de code source actuellement disponibles.

- [Architecture](../../extensibility/internals/source-control-plug-in-architecture.md)

 Utilise un diagramme d’architecture pour expliquer l’intégration d’un plug-in de contrôle de code source avec l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Guide de test](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Fournit des instructions sur le test de l’installation et du fonctionnement d’un plug-in de contrôle de code source.

## <a name="related-sections"></a>Sections connexes
- [Créer un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Explique comment créer un VSPackage de contrôle de code source qui fournit non seulement une fonctionnalité de contrôle de code source, mais remplace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur du contrôle de code source.

- [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)

 Fournit une liste complète de tous les éléments de l’API de plug-in de contrôle de code source.

- [Contrôle de code source](../../extensibility/internals/source-control.md)

 Décrit les options permettant d’implémenter le contrôle de code source en tant que fonctionnalité intégrée de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
