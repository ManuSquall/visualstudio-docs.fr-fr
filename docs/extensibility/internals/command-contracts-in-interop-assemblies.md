---
title: Contrats de commandement dans les assemblées Interop Microsoft Docs
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
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709683"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contrats de commandement dans les assemblées interop
Le contrat de base pour <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> le traitement des <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> commandes à travers l’interface est que l’environnement appelle la méthode pour déterminer si la commande est prise en charge et, si elle est prise en charge, pour déterminer son état et son texte. Ensuite, l’environnement <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> appelle la méthode pour exécuter la commande.

 La <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode est manipulée de façon identique pour toutes les commandes. Une communication plus poussée, si nécessaire (par exemple, avec <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> des listes d’abandon), est gérée en appelant la méthode avec des paramètres appropriés. L’interprétation de ces paramètres dépend de la commande spécifiée.

 Si la cible de commande renvoie les valeurs dans le paramètre de sortie, l’appelant est toujours responsable de la libération des ressources qui ont été allouées. Parce que ce paramètre est une variante, l’effacement de la variante libère les ressources.

 Dans les cas où les commandes <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> doivent fonctionner dans une fenêtre de hiérarchie, l’interface doit être utilisée. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> a un contrat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> similaire <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>avec des méthodes similaires: et .

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Itinéraire de commande dans VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Mise en œuvre du commandement](../../extensibility/internals/command-implementation.md)
