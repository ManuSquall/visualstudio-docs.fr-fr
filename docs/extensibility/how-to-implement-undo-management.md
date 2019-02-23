---
title: 'Procédure : Implémenter la gestion de l’annulation | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a896a5b850887b36a4fb6596923e742429c44dc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714125"
---
# <a name="how-to-implement-undo-management"></a>Procédure : Gestion d’annulation implémenter
L’interface principale utilisée pour la gestion de l’annulation est <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, qui est implémentée par l’environnement. Pour prendre en charge la gestion d’annulation, implémenter des unités d’annulation distinct (autrement dit, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, qui peut contenir plusieurs étapes individuelles.

 Façon dont vous implémentez la gestion de l’annulation varie selon que votre éditeur prend en charge plusieurs vues ou non. Les procédures pour chaque implémentation sont détaillées dans les sections suivantes.

## <a name="cases-where-an-editor-supports-a-single-view"></a>Cas où un éditeur prend en charge une seule vue
 Dans ce scénario, l’éditeur ne prend pas en charge plusieurs vues. Il y a qu’un seul éditeur et un seul document, et ils prennent en charge d’annulation. Utilisez la procédure suivante pour implémenter la gestion de l’annulation.

### <a name="to-support-undo-management-for-a-single-view-editor"></a>Pour prendre en charge la gestion d’annulation pour un éditeur avec affichage unique

1.  Appelez `QueryInterface` sur le `IServiceProvider` interface sur le frame de fenêtre pour `IOleUndoManager`, à partir de l’objet de vue de document pour accéder au gestionnaire d’annulation (`IID_IOLEUndoManager`).

2.  Lorsqu’une vue est placée dans un frame de fenêtre, elle obtient un pointeur de site, qu’elle peut utiliser pour appeler `QueryInterface` pour `IServiceProvider`.

## <a name="cases-where-an-editor-supports-multiple-views"></a>Cas où un éditeur prend en charge plusieurs vues
 Si vous avez la séparation de document et la vue, il est normalement un gestionnaire d’annulation associé au document lui-même. Toutes les unités d’annulation sont placées sur un gestionnaire d’annulation associé à l’objet de données de document.

 Au lieu de l’interrogation de l’affichage pour le Gestionnaire d’annulation, dont il en existe un pour chaque vue, les données du document object appelle <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> pour instancier le Gestionnaire d’annulation, en spécifiant un identificateur de classe de CLSID_OLEUndoManager. L’identificateur de classe est définie dans le *OCUNDOID.h* fichier.

 Lorsque vous utilisez <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> pour créer votre propre instance de gestionnaire d’annulation, utilisez la procédure suivante pour raccorder votre gestionnaire d’annulation de l’environnement.

### <a name="to-hook-your-undo-manager-into-the-environment"></a>Pour raccorder votre gestionnaire d’annulation de l’environnement

1. Appelez `QueryInterface` sur l’objet retourné par <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> pour `IID_IOleUndoManager`. Store le pointeur vers <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.

2. Appelez `QueryInterface` sur `IOleUndoManager` pour `IID_IOleCommandTarget`. Store le pointeur vers <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

3. Relais votre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> appelle stocké `IOleCommandTarget` interface pour les commandes StandardCommandSet97 suivantes :

   -   cmdidUndo

   -   cmdidMultiLevelUndo

   -   cmdidRedo

   -   cmdidMultiLevelRedo

   -   cmdidMultiLevelUndoList

   -   cmdidMultiLevelRedoList

4. Appelez `QueryInterface` sur `IOleUndoManager` pour `IID_IVsChangeTrackingUndoManager`. Store le pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.

    Utiliser le pointeur pour <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> pour appeler le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>et le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> méthodes.

5. Appelez `QueryInterface` sur `IOleUndoManager` pour `IID_IVsLinkCapableUndoManager`.

6. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> avec votre document, qui doit également implémenter le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interface. Lors de la fermeture du document, appelez `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.

7. Lors de la fermeture du document, appelez `QueryInterface` sur votre gestionnaire d’annulation pour `IID_IVsLifetimeControlledObject`.

8. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.

9. Lorsque des modifications sont apportées au document, appelez <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> sur le gestionnaire avec un `OleUndoUnit` classe. Le <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> méthode conserve une référence à l’objet, vous le relâchez généralement juste après le <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.

   Le `OleUndoManager` classe représente une instance de pile d’annulation unique. Par conséquent, il existe un objet de gestionnaire d’annulation par entité de données qui est suivie pour annuler ou rétablir.

> [!NOTE]
>  Tandis que l’objet de gestionnaire d’annulation est largement utilisé par l’éditeur de texte, il est un composant général qui ne prend en charge spécifique pour l’éditeur de texte. Si vous souhaitez prendre en charge plusieurs niveaux annulation ou rétablissement, vous pouvez utiliser cet objet pour ce faire.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>
- [Guide pratique pour Effacer la pile d’annulation](../extensibility/how-to-clear-the-undo-stack.md)