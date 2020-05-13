---
title: Création d’un plug-in de contrôle des sources Microsoft Docs
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
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709175"
---
# <a name="create-a-source-control-plug-in"></a>Créer un plug-in de contrôle source
Le Visual Studio SDK fournit des ressources qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous permettent d’ajouter une capacité de contrôle des sources à l’environnement de développement intégré (IDE). Il vous permet d’utiliser n’importe quel DLL plug-in qui se conforme à l’API de contrôle source Plug-in décrit dans cette documentation.

## <a name="in-this-section"></a>Contenu de cette section
- [Bien démarrer](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Décrit comment installer un plug-in de contrôle source et met en évidence les versions actuellement disponibles Source Control Plug-in API.

- [Architecture](../../extensibility/internals/source-control-plug-in-architecture.md)

 Utilise un diagramme d’architecture pour expliquer l’intégration [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] d’un plug-in de contrôle source avec l’IDE.

- [Guide d’essai](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Fournit des conseils sur la façon de tester l’installation et le fonctionnement d’un plug-in de contrôle de source.

## <a name="related-sections"></a>Sections connexes
- [Créer un contrôle source VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Discute de la façon de créer un contrôle source VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qui non seulement fournit la fonctionnalité de contrôle des sources, mais remplace l’interface utilisateur de contrôle des sources.

- [Plug-ins de contrôle des sources](../../extensibility/source-control-plug-ins.md)

 Fournit une liste complète de tous les éléments de l’API rechargeable de contrôle source.

- [Contrôle de code source](../../extensibility/internals/source-control.md)

 Discute des options pour mettre en œuvre le contrôle des sources comme une caractéristique intégrée de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
