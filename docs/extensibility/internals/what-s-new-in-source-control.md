---
title: Nouveauté dans le contrôle des sources dans le Visual Studio 2015 SDK (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703407"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Nouveauté dans le contrôle des sources pour le Visual Studio 2015 SDK

Dans [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]le , vous pouvez fournir une solution de contrôle source profondément intégrée en implémentant un contrôle source VSPackage. Cette section décrit les caractéristiques du contrôle des sources VSPackages et donne un aperçu des étapes de mise en œuvre.

## <a name="the-source-control-vspackage"></a>Le contrôle source VSPackage

Visual Studio prend en charge deux types de solutions de contrôle des sources. Dans toutes les versions de Visual Studio, vous pouvez toujours intégrer un plug-in à base d’API de contrôle source. Vous pouvez également créer un VSPackage pour le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] contrôle des sources qui fournit une intégration profonde, chemin adapté pour les solutions de contrôle des sources qui nécessitent un haut niveau de sophistication et d’autonomie.

Un VSPackage peut ajouter presque n’importe quel type de fonctionnalité à Visual Studio. Un contrôle source VSPackage fournit une fonctionnalité complète de contrôle source pour Visual Studio, de l’interface utilisateur présentée à l’utilisateur à la communication back-end avec le système de contrôle source.

La mise en œuvre d’un contrôle source VSPackage nécessite une stratégie « tout ou rien ». Le créateur d’un contrôle source VSPackage doit investir une quantité importante d’efforts dans la mise en œuvre d’un certain nombre d’interfaces de contrôle source et de nouveaux éléments d’interface utilisateur (boîtes de dialogue, menus et barres d’outils) pour couvrir l’ensemble des fonctionnalités de contrôle source, ainsi que les interfaces requises de tout paquet pour s’intégrer avec succès avec Visual Studio.

Les étapes suivantes donnent un aperçu général de ce qui est nécessaire pour mettre en œuvre un ensemble de contrôle des sources. Pour plus de détails, voir [Créer un contrôle source VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Créez un VSPackage qui offre un service privé de contrôle des sources.

2. Implémentez les interfaces dans les services liés au contrôle source <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> qui <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> sont proposés par Visual Studio (par exemple, l’interface et l’interface).

3. Enregistrez votre contrôle source VSPackage.

4. Implémenter toutes les interfaces utilisateur de contrôle des sources, y compris les éléments de menu, les boîtes de dialogue, les barres d’outils et les menus contextuels.

5. Tous les événements liés au contrôle des sources sont transmis à votre VSackage de contrôle source lorsqu’il est actif et doit être géré par votre VSPackage.

6. Votre contrôle source VSPackage doit écouter des <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> événements tels que ceux qui implémentent l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> ainsi que Track Project Document (TPD) événements (tel que mis en œuvre par l’interface) et prendre les mesures nécessaires.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Vue d’ensemble](../../extensibility/internals/source-control-integration-overview.md)
- [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)
