---
title: La mise à jour des valeurs de propriété dans la fenêtre Propriétés | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 0272ba348e29fb1a2a118a0ff4b0989a2aa1683f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501788"
---
# <a name="updating-property-values-in-the-properties-window"></a>Mise à jour des valeurs de propriété dans la fenêtre Propriétés
Il existe deux façons de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour. La première consiste à appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface, ce qui permet d’accéder aux fonctionnalités de base, y compris l’accès à et création de fenêtres Outil et document fournie par l’environnement. Les étapes qui suivent décrivent ce processus de synchronisation.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Mise à jour des valeurs de propriété à l’aide de l’interface IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Pour mettre à jour les valeurs de propriété à l’aide de l’interface IVsUIShell  
  
1.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (via <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service) quand un VSPackage, projets, ou l’éditeur doit créer ou énumérer des fenêtres Outil ou le document.  
  
2.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> pour conserver le **propriétés** fenêtre synchronisée avec les modifications apportées aux propriétés d’un projet (ou tout autre objet sélectionné parcouru par la **propriétés** fenêtre) sans avoir à implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> et le déclenchement <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> événements.  
  
3.  Implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> pour activer ou désactiver, respectivement, de notification du client des événements de hiérarchie sans nécessiter de la hiérarchie pour implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## <a name="updating-property-values-using-iconnection"></a>Mise à jour des valeurs de propriété à l’aide de l’interface IConnection  
 La deuxième façon de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour consiste à implémenter `IConnection` sur l’objet connectable pour indiquer l’existence des interfaces sortantes. Si vous souhaitez localiser le nom de propriété, dérivez votre objet de <xref:System.ComponentModel.ICustomTypeDescriptor>. Le <xref:System.ComponentModel.ICustomTypeDescriptor> implémentation peut modifier les descripteurs de propriété renvoyés et modifier le nom d’une propriété. Pour localiser la description, créer un attribut qui dérive de <xref:System.ComponentModel.DescriptionAttribute> et remplacez la propriété Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considérations relatives à l’implémentation de l’interface IConnection  
  
1.  `IConnection` fournit l’accès à un sous-objet énumérateur avec le <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. Il donne également accès à toutes les les connexion point sous-objets, chacun d’eux implémentant le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface.  
  
2.  Chaque objet est chargé d’implémenter un <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> événement. La fenêtre **Propriétés** affiche des conseils sur l’événement défini via `IConnection`.  
  
3.  Un point de connexion détermine le nombre de connexions (un ou plusieurs) autorise dans son implémentation de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un point de connexion qui ne permet qu’une seule interface peut retourner <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> à partir de la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> (méthode).  
  
4.  Un client peut appeler le `IConnection` interface pour obtenir l’accès à un sous-objet énumérateur avec le <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. Le <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface peut ensuite être appelée pour énumérer les points de connexion pour chaque interface sortante ID (IID).  
  
5.  `IConnection` peut également être appelée pour obtenir l’accès à la connexion sous-objets point avec le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface pour chaque IID sortant. Via le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface, un client démarre ou termine une boucle consultative avec l’objet connectable et la synchronisation du client. Le client peut également appeler le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface pour obtenir un objet énumérateur avec le <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interface pour énumérer les connexions qu’il connaît.  
  
## <a name="see-also"></a>Voir aussi  
 [Annonce de suivi de sélection de fenêtre de propriétés](../misc/announcing-property-window-selection-tracking.md)   
 [Extension des propriétés](../extensibility/internals/extending-properties.md)