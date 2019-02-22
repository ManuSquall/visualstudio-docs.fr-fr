---
title: Création d’un contrôle de Source de plug-in | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c33b852a585825f3c5b5fc415b01ac31e35f763f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606523"
---
# <a name="create-a-source-control-plug-in"></a>Créer un contrôle de source de plug-in
Le SDK Visual Studio fournit des ressources qui vous permettent d’ajouter la fonctionnalité de contrôle de code source pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Il vous permet d’utiliser une DLL de plug-in qui est conforme avec l’API de plug-in de contrôle de Source décrites dans cette documentation.

## <a name="in-this-section"></a>Dans cette section
- [Bien démarrer](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Décrit comment installer un plug-in de contrôle de code source et met en évidence les versions d’API de plug-in de contrôle de Source actuellement disponibles.

- [Architecture](../../extensibility/internals/source-control-plug-in-architecture.md)

 Utilise un diagramme d’architecture pour expliquer l’intégration d’un contrôle de source de plug-in avec la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Guide de test](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Fournit des conseils sur la façon de tester l’installation et le fonctionnement d’un plug-in de contrôle de code source.

## <a name="related-sections"></a>Rubriques connexes
- [Créer un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Explique comment créer un contrôle de code source VSPackage qui non seulement fournit des fonctionnalités de contrôle de code source, mais remplace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur de contrôle de code source.

- [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)

 Fournit une liste complète de tous les éléments dans l’API de plug-in de contrôle de Source.

- [Contrôle de code source](../../extensibility/internals/source-control.md)

 Décrit les options pour l’implémentation de contrôle de code source comme une fonctionnalité intégrée de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
