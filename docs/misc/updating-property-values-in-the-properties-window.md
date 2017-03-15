---
title: "Mise &#224; jour des valeurs de propri&#233;t&#233; dans la fen&#234;tre Propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Propriétés (fenêtre), mise à jour des valeurs de propriété"
  - "valeurs de propriété, mise à jour dans la fenêtre Propriétés"
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Mise &#224; jour des valeurs de propri&#233;t&#233; dans la fen&#234;tre Propri&#233;t&#233;s
Il existe deux façons de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour. La première consiste à appeler l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, qui donne accès aux fonctionnalités de base de fenêtrage, y compris l’utilisation et la création de fenêtres Outil et de document fournies par l’environnement. Les étapes qui suivent décrivent ce processus de synchronisation.  
  
## Mise à jour des valeurs de propriété à l’aide de l’interface IVsUIShell  
  
#### Pour mettre à jour les valeurs de propriété à l’aide de l’interface IVsUIShell  
  
1.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> \(via le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>\) quand un VSPackage, projet ou éditeur doit créer ou énumérer une fenêtre Outil ou de document.  
  
2.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> pour que la fenêtre **Propriétés** reste synchronisée avec les valeurs de propriété mises à jour pour un projet \(ou pour tout autre objet sélectionné affiché dans la fenêtre **Propriétés**\), sans implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> ni déclencher des événements <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>.  
  
3.  Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> pour activer ou désactiver, respectivement, la notification par le client des événements de la hiérarchie \(cette hiérarchie n’a alors pas besoin d’implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>\).  
  
## Mise à jour des valeurs de propriété à l’aide de l’interface IConnection  
 La deuxième façon de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour consiste à implémenter `IConnection` sur l’objet connectable pour indiquer l’existence des interfaces sortantes. Si vous souhaitez localiser le nom de propriété, dérivez votre objet de l’élément <xref:System.ComponentModel.ICustomTypeDescriptor>. L’implémentation de l’élément <xref:System.ComponentModel.ICustomTypeDescriptor> peut modifier les descripteurs de propriété renvoyés et modifier le nom d’une propriété. Pour localiser la description, créez un attribut dérivé de l’élément <xref:System.ComponentModel.DescriptionAttribute> et remplacez la propriété Description.  
  
#### Considérations relatives à l’implémentation de l’interface IConnection  
  
1.  `IConnection` fournit l’accès à un sous\-objet énumérateur avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Elle fournit aussi l’accès à tous les sous\-objets point de connexion, chacun d’eux implémentant l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.  
  
2.  Chaque objet parcouru doit implémenter un événement <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. La fenêtre **Propriétés** affiche des conseils sur l’événement défini via `IConnection`.  
  
3.  Un point de connexion détermine le nombre de connexions \(une seule ou plusieurs\) qu’il autorise dans son implémentation d’<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un point de connexion autorisant une seule interface peut renvoyer <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> de la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.  
  
4.  Un client peut appeler l’interface `IConnection` pour obtenir l’accès à un sous\-objet énumérateur avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. L’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> peut ensuite être appelée pour énumérer les points de connexion pour chaque ID d’interface sortante \(IID\).  
  
5.  L’interface `IConnection` peut également être appelée pour obtenir l’accès aux sous\-objets point de connexion avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pour chaque IID sortant. Via l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>, un client démarre ou arrête une boucle de conseil avec l’objet connectable et la synchronisation du client. Le client peut également appeler l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pour obtenir un objet énumérateur avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> qui énumère les connexions identifiées.  
  
## Voir aussi  
 [Annonce du suivi de sélection de la fenêtre Propriétés](/visual-cpp/misc/announcing-property-window-selection-tracking)   
 [Étendre les propriétés](../extensibility/internals/extending-properties.md)