---
title: Enregistrement d’un document personnalisé | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705617"
---
# <a name="saving-a-custom-document"></a>Enregistrement d’un document personnalisé
L’environnement gère les commandes **Save**, **Save As**et **Save all** . Lorsqu’un utilisateur clique sur **Enregistrer**, **Enregistrer sous**, **ou enregistrer tout** dans le menu **fichier** ou ferme la solution, ce qui entraîne un enregistrement tout, le processus suivant se produit.

 ![Éditeur du client-enregistrer](../../extensibility/internals/media/private.gif "Privées") Enregistrer, enregistrer sous et enregistrer la gestion de toutes les commandes pour un éditeur personnalisé

 Ce processus est détaillé dans les étapes suivantes :

1. Pour les commandes **Enregistrer** et **Enregistrer sous** , l’environnement utilise le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service pour déterminer la fenêtre de document active et, par conséquent, les éléments à enregistrer. Une fois que la fenêtre de document active est connue, l’environnement recherche le pointeur de hiérarchie et l’identificateur d’élément (itemID) du document dans la table de document en cours d’exécution. Pour plus d’informations, consultez exécution de la [table des documents](../../extensibility/internals/running-document-table.md).

     Pour la commande Enregistrer tout, l’environnement utilise les informations contenues dans la table de document en cours d’exécution pour compiler la liste de tous les éléments à enregistrer.

2. Lorsque la solution reçoit un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> appel, elle itère au sein de l’ensemble d’éléments sélectionnés (autrement dit, les sélections multiples exposées par le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service).

3. Sur chaque élément de la sélection, la solution utilise le pointeur de hiérarchie pour appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> méthode afin de déterminer si la commande de menu enregistrer doit être activée. Si un ou plusieurs éléments sont modifiés, la commande Enregistrer est activée. Si la hiérarchie utilise un éditeur standard, la hiérarchie délègue l’interrogation de l’état de modification à l’éditeur en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> méthode.

4. Sur chaque élément sélectionné qui est modifié, la solution utilise le pointeur de hiérarchie pour appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> méthode sur les hiérarchies appropriées.

     Dans le cas d’un éditeur personnalisé, la communication entre l’objet de données de document et le projet est privée. Ainsi, tous les problèmes de persistance spéciaux sont traités entre ces deux objets.

    > [!NOTE]
    > Si vous implémentez votre propre persistance, veillez à appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> méthode pour gagner du temps. Cette méthode vérifie que le fichier peut être enregistré en toute sécurité (par exemple, si le fichier n’est pas en lecture seule).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)
