---
title: "Contrats de commande dans les assemblys d&#39;interop&#233;rabilit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commande de traitement avec des assemblys PIA, les contrats de commande"
  - "assemblys PIA, les contrats de commande"
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Contrats de commande dans les assemblys d&#39;interop&#233;rabilit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le contrat de base pour la gestion des commandes via le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface est que l'environnement appelle le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode pour déterminer si la commande est prise en charge et, si elle est prise en charge, afin de déterminer son état et le texte. Ensuite, l'environnement appelle le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode pour exécuter la commande.  
  
 Le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \(méthode\) est gérée de façon identique pour toutes les commandes. Communication supplémentaire, si nécessaire \(par exemple, avec des listes déroulantes\), est gérée en appelant le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode avec les paramètres appropriés. L'interprétation de ces paramètres dépend de la commande spécifiée.  
  
 Si la cible de commande retourne les valeurs dans le paramètre de sortie, l'appelant est toujours chargé de libérer toutes les ressources qui avaient été alloués. Étant donné que ce paramètre est une variante, désactivant la variante libère les ressources.  
  
 Dans les cas où les commandes doivent fonctionner dans une fenêtre de la hiérarchie, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface doit être utilisée. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface dispose d'un contrat similaire avec des méthodes similaires : <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## Voir aussi  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routage des commandes dans les packages VS](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implémentation](../../extensibility/internals/command-implementation.md)