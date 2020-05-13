---
title: Enregistrement d’un document personnalisé (en anglais) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705617"
---
# <a name="saving-a-custom-document"></a>Enregistrement d’un document personnalisé
L’environnement gère **l’Enregistrer**, **Enregistrer comme**, et enregistrer toutes **les** commandes. Lorsqu’un utilisateur clique **sur Enregistrer,** **enregistrer comme**, ou **enregistrer tous** sur le menu **De fichier** ou ferme la solution, résultant en un Enregistrement Tous, le processus suivant se produit.

 ![Client Editor Save](../../extensibility/internals/media/private.gif "Privé") Enregistrer, enregistrer as et enregistrer toute la manipulation de commande pour un éditeur personnalisé

 Ce processus est détaillé dans les étapes suivantes :

1. Pour les commandes **Save** and **Save As,** l’environnement utilise le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service pour déterminer la fenêtre de document active et donc quels éléments doivent être enregistrés. Une fois que la fenêtre de document active est connue, l’environnement trouve le pointeur de hiérarchie et l’identifiant d’élément (itemID) pour le document dans la table de document en cours d’exécution. Pour plus d’informations, voir [Tableau des documents d’exécution](../../extensibility/internals/running-document-table.md).

     Pour la commande Save All, l’environnement utilise les informations contenues dans le tableau de document en cours d’exécution pour compiler la liste de tous les éléments à enregistrer.

2. Lorsque la solution <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> reçoit un appel, elle s’isère à travers l’ensemble <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> d’éléments sélectionnés (c’est-à-dire les sélections multiples exposées par le service).

3. Sur chaque élément de la sélection, la solution <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> utilise le pointeur de hiérarchie pour appeler la méthode pour déterminer si la commande de menu Enregistrer doit être activée. Si un ou plusieurs articles sont sales, la commande Save est activée. Si la hiérarchie utilise un éditeur standard, alors la hiérarchie délègue <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> le statut sale à l’éditeur en appelant la méthode.

4. Sur chaque élément sélectionné qui est sale, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> solution utilise le pointeur de hiérarchie pour appeler la méthode sur les hiérarchies appropriées.

     Dans le cas d’un éditeur personnalisé, la communication entre l’objet de données documentaires et le projet est privée. Ainsi, toutes les préoccupations particulières de persistance sont traitées entre ces deux objets.

    > [!NOTE]
    > Si vous implémentez votre propre <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> persistance, assurez-vous d’appeler la méthode pour gagner du temps. Cette méthode vérifie pour s’assurer qu’il est sûr d’enregistrer le fichier (par exemple, le fichier n’est pas lu uniquement).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)
