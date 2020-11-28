---
title: Contrats de commande dans les assemblys d’interopérabilité | Microsoft Docs
description: En savoir plus sur le contrat de base pour la gestion des commandes par le biais de l’interface Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d655bfb3e6f2206156cd3a6d091ea04f18afe91a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304910"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contrats de commande dans les assemblys d’interopérabilité
Le contrat de base pour la gestion des commandes par le biais de l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface est que l’environnement appelle la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode pour déterminer si la commande est prise en charge et, si elle est prise en charge, pour déterminer son état et son texte. L’environnement appelle ensuite la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode pour exécuter la commande.

 La <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode est gérée de façon identique pour toutes les commandes. Des communications supplémentaires, si nécessaire (par exemple, avec des listes déroulantes), sont gérées en appelant la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode avec les paramètres appropriés. L’interprétation de ces paramètres dépend de la commande spécifiée.

 Si la cible de la commande retourne des valeurs dans le paramètre de sortie, l’appelant est toujours responsable de la libération des ressources allouées. Étant donné que ce paramètre est un variant, l’effacement de la variante libère les ressources.

 Dans les cas où les commandes doivent fonctionner dans une fenêtre de hiérarchie, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface doit être utilisée. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface a un contrat similaire avec des méthodes similaires : <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>Voir aussi
- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routage des commandes dans les VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implémentation de la commande](../../extensibility/internals/command-implementation.md)
