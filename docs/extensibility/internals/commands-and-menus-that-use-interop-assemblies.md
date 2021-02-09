---
title: Commandes et menus qui utilisent des assemblys d’interopérabilité | Microsoft Docs
description: Découvrez les tâches qui doivent être effectuées lors de l’implémentation de commandes de menu et de barre d’outils dans un VSPackage à l’aide d’assemblys d’interopérabilité.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ea48c77212927c14b4ad49c91ce2f4d988e36f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928222"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Commandes et menus qui utilisent des assemblys d’interopérabilité
Un VSPackage qui implémente des commandes de menu et de barre d’outils à l’aide d’assemblys d’interopérabilité doit :

- Informez l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE) sur les commandes qu’il prend en charge et s’il est actuellement activé.

- Respectez les règles (contrat) pour la gestion des commandes.

- Implémentez explicitement la gestion des commandes à l’aide de l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface ou.

  La section suivante décrit comment effectuer ces tâches.

## <a name="in-this-section"></a>Dans cette section
- [Déterminer l’état de la commande à l’aide d’assemblys d’interopérabilité](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Décrit comment un VSPackage informe l’IDE sur les commandes qu’il prend en charge et s’il est actuellement activé.

- [Contrats de commande dans les assemblys d’interopérabilité](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Fournit une définition du contrat de commande de base utilisé par tous les VSPackages qui implémentent des commandes à l’aide d’assemblys d’interopérabilité.

- [Implémentation de la commande](../../extensibility/internals/command-implementation.md)

 Fournit une vue d’ensemble de la façon dont un VSPackage implémente une commande.

- [Inscrire des gestionnaires de commandes d’assembly d’interopérabilité](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Décrit les entrées de Registre requises pour notifier l’IDE qu’un VSPackage fournit un gestionnaire de commandes.

## <a name="related-sections"></a>Sections connexes
- [Disponibilité des commandes](../../extensibility/internals/command-availability.md)

 Décrit les critères utilisés par l’IDE pour déterminer les commandes VSPackage disponibles et l’objet qui les gère.

- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Fournit des détails sur la création d’une interface utilisateur qui utilise la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prise en charge des commandes.

- [Routage des commandes dans les VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Vue d’ensemble du processus utilisé pour associer un objet à la demande de commande correcte.
