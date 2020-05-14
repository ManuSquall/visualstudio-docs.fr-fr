---
title: Commandes et menus qui utilisent des assemblées Interop Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709486"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Commandes et menus qui utilisent des assemblages Interop
Un VSPackage qui implémente les commandes de menu et de barre d’outils en utilisant des assemblages Interop doit :

- Informez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) sur les commandes qu’il prend en charge et si elles sont actuellement activées.

- Respectez les règles (contrat) pour le traitement des commandes.

- Implémentez explicitement la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> manipulation des commandes en utilisant l’interface ou l’interface.

  La section suivante décrit comment effectuer ces tâches.

## <a name="in-this-section"></a>Contenu de cette section
- [Déterminer l’état de commande en utilisant des assemblages Interop](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Décrit comment un VSPackage informe l’IDE sur les commandes qu’il prend en charge et si elles sont actuellement activées.

- [Contrats de commandement dans les assemblées Interop](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Fournit une définition du contrat de commande de base utilisé par tous les VSPackages implémentant les commandes à l’aide d’assemblages Interop.

- [Mise en œuvre du commandement](../../extensibility/internals/command-implementation.md)

 Fournit un aperçu de la façon dont un VSPackage implémente une commande.

- [Enregistrez les gestionnaires de commande d’assemblage Interop](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Décrit les entrées de registre nécessaires pour aviser l’IDE qu’un VSPackage fournit un gestionnaire de commande.

## <a name="related-sections"></a>Sections connexes
- [Disponibilité de commande](../../extensibility/internals/command-availability.md)

 Décrit les critères utilisés par l’IDE pour déterminer quelles commandes VSPackage sont disponibles et quel objet les gère.

- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Fournit des détails sur la façon [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de créer une interface utilisateur qui utilise le support de commande.

- [Itinéraire de commande dans VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Un aperçu du processus utilisé pour relier un objet à la demande de commande correcte.
