---
title: Nouveautés du contrôle de code source dans le kit de développement logiciel (SDK) Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703407"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Nouveautés du contrôle de code source pour le kit de développement logiciel (SDK) Visual Studio 2015

Dans [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , vous pouvez fournir une solution de contrôle de code source profondément intégrée en implémentant un VSPackage de contrôle de code source. Cette section décrit les fonctionnalités des VSPackages de contrôle de code source et fournit une vue d’ensemble des étapes d’implémentation.

## <a name="the-source-control-vspackage"></a>VSPackage de contrôle de code source

Visual Studio prend en charge deux types de solutions de contrôle de code source. Dans toutes les versions de Visual Studio, vous pouvez toujours intégrer un plug-in basé sur une API de plug-in de contrôle de code source. Vous pouvez également créer un VSPackage pour le contrôle de code source qui fournit une intégration profonde, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] adaptée aux solutions de contrôle de code source qui requièrent un haut niveau de sophistication et d’autonomie.

Un VSPackage peut ajouter presque tous les types de fonctionnalités à Visual Studio. Un VSPackage de contrôle de code source fournit une fonctionnalité de contrôle de code source complète pour Visual Studio, de l’interface utilisateur présentée à l’utilisateur à la communication de serveur principal avec le système de contrôle de code source.

L’implémentation d’un VSPackage de contrôle de code source requiert une stratégie « tout ou rien ». Le créateur d’un VSPackage de contrôle de code source doit investir beaucoup d’efforts dans l’implémentation d’un certain nombre d’interfaces de contrôle de code source et de nouveaux éléments d’interface utilisateur (boîtes de dialogue, menus et barres d’outils) pour couvrir l’ensemble des fonctionnalités de contrôle de code source, ainsi que les interfaces nécessaires à l’intégration avec Visual Studio avec succès.

Les étapes suivantes fournissent une vue d’ensemble de ce qui est nécessaire pour implémenter un package de contrôle de code source. Pour plus d’informations, consultez [création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Créez un VSPackage qui offre un service de contrôle de code source privé.

2. Implémentez les interfaces dans les services liés au contrôle de code source qui sont offertss par Visual Studio (par exemple, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interface et).

3. Inscrivez votre VSPackage de contrôle de code source.

4. Implémentez toutes les interfaces utilisateur du contrôle de code source, notamment les éléments de menu, les boîtes de dialogue, les barres d’outils et les menus contextuels.

5. Tous les événements liés au contrôle de code source sont passés à votre contrôle de code source VSackage lorsqu’il est actif et doivent être gérés par votre VSPackage.

6. Votre VSPackage de contrôle de code source doit écouter les événements tels que ceux qui implémentent l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interface, ainsi que suivre les événements du document de projet (TPD) (implémenté par l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interface) et prendre les mesures nécessaires.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Vue d'ensemble](../../extensibility/internals/source-control-integration-overview.md)
- [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)
