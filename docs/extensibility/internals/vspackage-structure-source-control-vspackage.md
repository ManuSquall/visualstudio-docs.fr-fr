---
title: Structure VSPackage (VSPackage de contrôle de code source) | Microsoft Docs
description: En savoir plus sur le kit de développement logiciel (SDK) du package de contrôle de code source, qui fournit des instructions pour un VSPackage avec un implémenteur de contrôle de code source à intégrer à Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b95c382342675d79c0c6e854b5fc087d495827e2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898820"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Structure VSPackage (VSPackage de contrôle de code source)

Le kit de développement logiciel (SDK) du package de contrôle de code source fournit des instructions pour créer un VSPackage qui permet à un implémenteur de contrôle de code source d’intégrer ses fonctionnalités de contrôle de code source à l’environnement Visual Studio. Un VSPackage est un composant COM qui est généralement chargé à la demande par l’environnement de développement intégré (IDE) de Visual Studio en fonction des services publiés par le package dans ses entrées de registre. Chaque VSPackage doit implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Un VSPackage consomme généralement des services offerts par l’IDE de Visual Studio et offre certains services de lui-même.

Un VSPackage déclare ses éléments de menu et établit un état d’élément par défaut par le biais du fichier. vsct. L’IDE de Visual Studio affiche les éléments de menu dans cet État jusqu’à ce que le VSPackage soit chargé. Par la suite, l’implémentation du VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode est appelée pour activer ou désactiver les éléments de menu.

## <a name="source-control-package-characteristics"></a>Caractéristiques du package de contrôle de code source

Un VSPackage de contrôle de code source est profondément intégré à Visual Studio. La sémantique VSPackage inclut les éléments suivants :

- Interface à implémenter en raison d’un VSPackage (l' `IVsPackage` interface)

- Implémentation de la commande d’interface utilisateur (fichier. vsct et implémentation de l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface)

- Inscription du VSPackage avec Visual Studio.

Le VSPackage de contrôle de code source doit communiquer avec ces autres entités Visual Studio :

- Projets

- Éditeurs

- Solutions

- Windows

- Table de document en cours d’exécution

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Services de l’environnement Visual Studio qui peuvent être utilisés

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Service SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfaces VSIP implémentées et appelées

Un package de contrôle de code source est un VSPackage et, par conséquent, il peut interagir directement avec d’autres VSPackages inscrits auprès de Visual Studio. Pour fournir toutes les fonctionnalités de contrôle de code source, un VSPackage de contrôle de code source peut traiter les interfaces fournies par les projets ou l’interpréteur de commandes.

Chaque projet dans Visual Studio doit implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> pour être reconnu en tant que projet dans l’IDE de Visual Studio. Toutefois, cette interface n’est pas suffisamment spécialisée pour le contrôle de code source. Les projets qui sont censés être sous le contrôle de code source implémentent <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Cette interface est utilisée par le VSPackage de contrôle de code source pour interroger un projet et lui fournir des glyphes et des informations de liaison (les informations nécessaires pour établir une connexion entre l’emplacement du serveur et l’emplacement du disque d’un projet qui est sous contrôle de code source).

Le VSPackage de contrôle de code source implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , qui à son tour permet aux projets de s’inscrire pour le contrôle de code source et de récupérer leurs glyphes d’État.

Pour obtenir la liste complète des interfaces qu’un VSPackage de contrôle de code source doit prendre en compte, consultez [services et interfaces associés](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Voir aussi

- [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfaces et services associés](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
