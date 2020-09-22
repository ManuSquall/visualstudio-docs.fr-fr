---
title: 'Comment : implémenter la gestion des annulations | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840150"
---
# <a name="how-to-implement-undo-management"></a>Guide pratique pour implémenter la gestion des opérations d’annulation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’interface principale utilisée pour la gestion des annulations est <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> , qui est implémentée par l’environnement. Pour prendre en charge la gestion des annulations, implémentez des unités d’annulation distinctes (c’est-à-dire, qui <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> peuvent contenir plusieurs étapes individuelles.  
  
 La façon dont vous implémentez la gestion des annulations varie selon que votre éditeur prend ou non en charge plusieurs vues. Les procédures pour chaque implémentation sont détaillées dans les sections suivantes.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Cas où un éditeur prend en charge une vue unique  
 Dans ce scénario, l’éditeur ne prend pas en charge plusieurs vues. Il n’existe qu’un seul éditeur et un seul document, et ils prennent en charge l’annulation. Utilisez la procédure suivante pour implémenter la gestion des annulations.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Pour prendre en charge la gestion des annulations pour un éditeur unique  
  
1. Appelez `QueryInterface` sur l' `IServiceProvider` interface dans le frame de fenêtre pour `IOleUndoManager` , à partir de l’objet de vue de document pour accéder au gestionnaire d’annulation ( `IID_IOLEUndoManager` ).  
  
2. Lorsqu’une vue est sur un frame de fenêtre, elle obtient un pointeur de site, qu’elle peut utiliser pour appeler `QueryInterface` `IServiceProvider` .  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Cas où un éditeur prend en charge plusieurs vues  
 Si vous disposez d’une séparation de document et de vue, il existe normalement un gestionnaire d’annulation associé au document lui-même. Toutes les unités d’annulation sont placées sur un gestionnaire d’annulation associé à l’objet de données de document.  
  
 Au lieu de l’interrogation de la vue pour le gestionnaire d’annulation, dont il existe un pour chaque vue, l’objet de données du document appelle <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> pour instancier le gestionnaire d’annulation, en spécifiant un identificateur de classe de CLSID_OLEUndoManager. L’identificateur de classe est défini dans le fichier OCUNDOID. h.  
  
 Lorsque vous utilisez <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> pour créer votre propre instance du gestionnaire d’annulation, utilisez la procédure suivante pour raccorder votre gestionnaire d’annulations à l’environnement.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Pour raccorder votre gestionnaire d’annulations à l’environnement  
  
1. Appelez `QueryInterface` sur l’objet retourné par <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> pour `IID_IOleUndoManager` . Stocke le pointeur sur <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> .  
  
2. Appelez `QueryInterface` sur `IOleUndoManager` pour `IID_IOleCommandTarget` . Stocke le pointeur sur <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
3. Relayez votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> appelle l’interface stockée `IOleCommandTarget` pour les commandes StandardCommandSet97 suivantes :  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. Appelez `QueryInterface` sur `IOleUndoManager` pour `IID_IVsChangeTrackingUndoManager` . Stocke le pointeur sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> .  
  
    Utilisez le pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> pour appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> et les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> méthodes.  
  
5. Appelez `QueryInterface` sur `IOleUndoManager` pour `IID_IVsLinkCapableUndoManager` .  
  
6. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> avec votre document, qui doit également implémenter l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interface. Lorsque votre document est fermé, appelez `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` .  
  
7. Lorsque votre document est fermé, appelez `QueryInterface` sur votre gestionnaire d’annulation pour `IID_IVsLifetimeControlledObject` .  
  
8. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Lorsque des modifications sont apportées au document, appelez <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> sur le gestionnaire avec une `OleUndoUnit` classe. La <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> méthode conserve une référence à l’objet. par conséquent, vous la publiez en général juste après <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> .  
  
   La `OleUndoManager` classe représente une seule instance de la pile d’annulations. Par conséquent, il existe un objet gestionnaire d’annulation par entité de données qui est suivi pour l’annulation ou la restauration par progression.  
  
> [!NOTE]
> Bien que l’objet gestionnaire d’annulation soit largement utilisé par l’éditeur de texte, il s’agit d’un composant général qui n’a pas de prise en charge spécifique pour l’éditeur de texte. Si vous souhaitez prendre en charge l’annulation ou la restauration à plusieurs niveaux, vous pouvez utiliser cet objet pour ce faire.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Guide pratique pour effacer la pile des opérations d’annulation](../extensibility/how-to-clear-the-undo-stack.md)
