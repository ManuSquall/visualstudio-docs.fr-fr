---
title: "Comment : impl&#233;menter la gestion de l&#39;annulation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - Annuler gestion"
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Comment : impl&#233;menter la gestion de l&#39;annulation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'interface principale utilisée pour la gestion d'annulation est <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, implémentée par l'environnement.  Pour prendre en charge la gestion d'annulation, implémentez les unités séparées undo \(autrement dit, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, qui peut contenir plusieurs des étapes différentes.  
  
 La manière dont vous implémentez la gestion d'annulation varie selon que vos vues provenant d'éditeur plusieurs ou pas.  les procédures pour chaque implémentation sont détaillées dans les sections suivantes.  
  
## cas où un éditeur prend en charge une vue unique  
 Dans ce scénario, l'éditeur ne prend pas en charge plusieurs affichages.  Il n'existe qu'un éditeur et un document, et ils prennent en charge l'annulation.  Utilisez la procédure suivante pour implémenter la gestion d'annulation.  
  
#### Pour prendre en charge la gestion d'annulation pour un éditeur d'unique\-vue  
  
1.  Appelez `QueryInterface` à l'interface d' `IServiceProvider` sur le frame de fenêtre pour `IOleUndoManager`, de l'objet de vue du document pour accéder au gestionnaire de commandes undo \(`IID_IOLEUndoManager`\).  
  
2.  Lorsqu'une vue se trouve dans un frame de fenêtre, elle obtient un pointeur de site, qu'il peut utiliser pour appeler `QueryInterface` pour `IServiceProvider`.  
  
## Cas où un éditeur prend en charge plusieurs affichages  
 Si vous avez le document et séparation de vue, il y a généralement un gestionnaire d'annulation associé au document lui\-même.  Toutes les unités undo sont placées dans un gestionnaire d'annulation associé à l'objet de données du document.  
  
 Au lieu de la vue recherchant le gestionnaire d'annulation, dont il existe un pour chaque affichage, l'objet de données du document appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> pour instancier le gestionnaire d'annulation, en spécifiant un identificateur de classe de CLSID\_OLEUndoManager.  l'identificateur de classe est défini dans le fichier d'OCUNDOID.h.  
  
 En utilisant l' <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> pour créer votre propre instance du gestionnaire d'annulation, utilisez la procédure suivante pour connecter votre gestionnaire d'annulation à l'environnement.  
  
#### Pour connecter votre gestionnaire d'annulation dans l'environnement  
  
1.  appelez `QueryInterface` sur l'objet retourné d' <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> pour `IID_IOleUndoManager`.  enregistrez le pointeur à <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  appelez `QueryInterface` sur `IOleUndoManager` pour `IID_IOleCommandTarget`.  enregistrez le pointeur à <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Escalader par effectuer votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et appels d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> dans l'interface stockée d' `IOleCommandTarget` pour les commandes StandardCommandSet97 suivantes :  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Appelez `QueryInterface` à `IOleUndoManager` pour `IID_IVsChangeTrackingUndoManager`.  enregistrez le pointeur à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Utilisez le pointeur à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> pour appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>, et les méthodes d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5.  Appelez `QueryInterface` à `IOleUndoManager` pour `IID_IVsLinkCapableUndoManager`.  
  
6.  Appelez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> avec votre document, qui doit également implémenter l'interface de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> .  Lorsque la fermeture du document, appelez `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  Lorsque la fermeture du document, appelez `QueryInterface` sur votre gestionnaire d'annulation pour `IID_IVsLifetimeControlledObject`.  
  
8.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Lorsque des modifications sont apportées au document, appelez <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> dans le gestionnaire avec une classe d' `OleUndoUnit` .  La méthode d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> conserve une référence à l'objet, et en général vous version il juste après <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 La classe d' `OleUndoManager` représente une instance unique de pile d'annulations.  Par conséquent, il existe un objet de gestionnaire d'annulation par entité de données est suivie pour l'annulation ou la de rétablissement.  
  
> [!NOTE]
>  Alors que l'objet de gestionnaire d'annulation est largement utilisé par l'éditeur de texte, il s'agit d'un composant général qui n'a pas d'assistance spécifique de l'éditeur de texte.  Si vous souhaitez prendre en charge l'annulation multiniveau ou la phase de rétablissement, vous pouvez utiliser cet objet pour le faire.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Comment : effacer la pile d'annulation](../extensibility/how-to-clear-the-undo-stack.md)