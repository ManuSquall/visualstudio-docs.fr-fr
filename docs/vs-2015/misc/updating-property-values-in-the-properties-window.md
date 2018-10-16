---
title: La mise à jour des valeurs de propriété dans la fenêtre Propriétés | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 8db48e1f746afa8f8f219935555815587ce5823c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290483"
---
# <a name="updating-property-values-in-the-properties-window"></a>Mise à jour des valeurs de propriété dans la fenêtre Propriétés
Il existe deux façons de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour. La première consiste à appeler l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, qui donne accès aux fonctionnalités de base de fenêtrage, y compris l’utilisation et la création de fenêtres Outil et de document fournies par l’environnement. Les étapes qui suivent décrivent ce processus de synchronisation.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Mise à jour des valeurs de propriété à l’aide de l’interface IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Pour mettre à jour les valeurs de propriété à l’aide de l’interface IVsUIShell  
  
1.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (via le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) quand un VSPackage, projet ou éditeur doit créer ou énumérer une fenêtre Outil ou de document.  
  
2.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> pour conserver le **propriétés** fenêtre synchronisée avec les modifications apportées aux propriétés d’un projet (ou tout autre objet sélectionné parcouru par la **propriétés** fenêtre) sans avoir à implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> et le déclenchement <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> événements.  
  
3.  Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> pour activer ou désactiver, respectivement, la notification par le client des événements de la hiérarchie (cette hiérarchie n’a alors pas besoin d’implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>).  
  
## <a name="updating-property-values-using-iconnection"></a>Mise à jour des valeurs de propriété à l’aide de l’interface IConnection  
 La deuxième façon de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour consiste à implémenter `IConnection` sur l’objet connectable pour indiquer l’existence des interfaces sortantes. Si vous souhaitez localiser le nom de propriété, dérivez votre objet de l’élément <xref:System.ComponentModel.ICustomTypeDescriptor>. L’implémentation de l’élément <xref:System.ComponentModel.ICustomTypeDescriptor> peut modifier les descripteurs de propriété renvoyés et modifier le nom d’une propriété. Pour localiser la description, créez un attribut dérivé de l’élément <xref:System.ComponentModel.DescriptionAttribute> et remplacez la propriété Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considérations relatives à l’implémentation de l’interface IConnection  
  
1.  `IConnection` fournit l’accès à un sous-objet énumérateur avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Elle fournit aussi l’accès à tous les sous-objets point de connexion, chacun d’eux implémentant l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.  
  
2.  Chaque objet parcouru doit implémenter un événement <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. La fenêtre **Propriétés** affiche des conseils sur l’événement défini via `IConnection`.  
  
3.  Un point de connexion détermine le nombre de connexions (une seule ou plusieurs) qu’il autorise dans son implémentation d’<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un point de connexion autorisant une seule interface peut renvoyer <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> de la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.  
  
4.  Un client peut appeler l’interface `IConnection` pour obtenir l’accès à un sous-objet énumérateur avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. L’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> peut ensuite être appelée pour énumérer les points de connexion pour chaque ID d’interface sortante (IID).  
  
5.  L’interface `IConnection` peut également être appelée pour obtenir l’accès aux sous-objets point de connexion avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pour chaque IID sortant. Via l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>, un client démarre ou arrête une boucle de conseil avec l’objet connectable et la synchronisation du client. Le client peut également appeler l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pour obtenir un objet énumérateur avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> qui énumère les connexions identifiées.  
  
## <a name="see-also"></a>Voir aussi  
 [Annonce de suivi de sélection de fenêtre de propriétés](../misc/announcing-property-window-selection-tracking.md)   
 [Extension des propriétés](../extensibility/internals/extending-properties.md)