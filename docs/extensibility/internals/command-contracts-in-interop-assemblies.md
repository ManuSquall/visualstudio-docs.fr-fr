---
title: Commande de contrats dans les assemblys PIA | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfb60bb4fdc0a633ecee92c47b8465f794416bec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127373"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contrats de commande dans des assemblys d’interopérabilité
Le contrat de base pour la gestion des commandes via le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface est que l’environnement appelle le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode pour déterminer si la commande est prise en charge et, si elle est prise en charge, afin de déterminer son état et le texte. Ensuite, l’environnement appelle le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode pour exécuter la commande.  
  
 Le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode est gérée de façon identique pour toutes les commandes. Les communications ultérieures, si nécessaire (par exemple, avec les listes déroulantes), sont gérée en appelant le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode avec les paramètres appropriés. L’interprétation de ces paramètres dépend de la commande spécifiée.  
  
 Si la cible de commande retourne les valeurs dans le paramètre de sortie, l’appelant est toujours chargé de libérer des ressources qui avaient été alloués. Étant donné que ce paramètre est une variante, effacer la variante libère les ressources.  
  
 Dans les cas où les commandes doivent fonctionner dans une fenêtre de la hiérarchie, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface doit être utilisée. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface a un contrat similaire avec des méthodes semblables : <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les VSPackages ajouter les éléments d’Interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routage des commandes dans des VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implémentation](../../extensibility/internals/command-implementation.md)