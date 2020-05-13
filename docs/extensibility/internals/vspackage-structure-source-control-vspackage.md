---
title: Structure VSPackage (Source Control VSPackage) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703806"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Structure VSPackage (VSPackage de contrôle de code source)

Le source Control Package SDK fournit des lignes directrices pour la création d’un VSPackage qui permet à un implémenteur de contrôle source d’intégrer sa fonctionnalité de contrôle source avec l’environnement Visual Studio. Un VSPackage est un composant COM qui est généralement chargé à la demande par l’environnement de développement intégré Visual Studio (IDE) basé sur les services qui sont annoncés par le paquet dans ses entrées de registre. Chaque VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>doit implémenter . Un VSPackage consomme généralement des services offerts par le Visual Studio IDE et offre certains services de ses propres.

Un VSPackage déclare ses éléments de menu et établit un état d’élément par défaut via le fichier .vsct. L’IDE Visual Studio affiche les éléments du menu dans cet état jusqu’à ce que le VSPackage soit chargé. Par la suite, la mise <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> en œuvre de la méthode par le VSPackage est appelée pour activer ou désactiver les éléments du menu.

## <a name="source-control-package-characteristics"></a>Caractéristiques du paquet de contrôle des sources

Un contrôle source VSPackage est profondément intégré dans Visual Studio. La sémantique VSPackage comprend :

- Interface à mettre en œuvre en `IVsPackage` vertu d’être un VSPackage (l’interface)

- Implémentation de commandement de l’interface (.fichier vsct et mise en œuvre de l’interface) <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>

- Enregistrement du VSPackage auprès de Visual Studio.

Le contrôle source VSPackage doit communiquer avec ces autres entités Visual Studio :

- Projets

- Éditeurs

- Solutions

- Windows

- La table de document en cours d’exécution

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Services d’environnement de studio visuel qui peuvent être consommés

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider Service

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfaces VSIP mises en œuvre et appelées

Un package de contrôle source est un VSPackage, et donc il peut interagir directement avec d’autres VSPackages qui sont enregistrés auprès de Visual Studio. Afin de fournir toute l’étendue de la fonctionnalité de contrôle des sources, un contrôle source VSPackage peut traiter les interfaces fournies par les projets ou la coquille.

Chaque projet de Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Studio doit être mis en œuvre pour être reconnu comme un projet au sein de l’IDE Visual Studio. Cependant, cette interface n’est pas assez spécialisée pour le contrôle des sources. Projets qui devraient être sous <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>contrôle source implémenter . Cette interface est utilisée par la source de contrôle VSPackage pour interroger un projet pour son contenu et pour lui fournir des glyphes et des informations contraignantes (les informations nécessaires pour établir une connexion entre l’emplacement du serveur et l’emplacement du disque d’un projet qui est sous contrôle source).

Le contrôle source VSPackage implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, ce qui permet aux projets de s’enregistrer pour le contrôle de la source et de récupérer leurs glyphes de statut.

Pour une liste complète des interfaces qu’une source de contrôle VSPackage doit considérer, voir [services et interfaces connexes](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Voir aussi

- [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfaces et services associés](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
