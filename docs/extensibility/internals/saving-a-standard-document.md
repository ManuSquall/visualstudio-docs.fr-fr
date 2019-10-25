---
title: Enregistrement d’un document standard | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df93813d339a45689845b82fe4f5a185301b6c74
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724096"
---
# <a name="saving-a-standard-document"></a>Enregistrement d’un document standard
L’environnement gère les commandes Save, Save As et Save all. Lorsqu’un utilisateur sélectionne **Enregistrer**, **Enregistrer sous**ou **enregistrer tout** à partir du menu **fichier** ou ferme la solution, ce qui entraîne un **enregistrement tout**, le processus suivant se produit.

 ![Éditeur standard](../../extensibility/internals/media/public.gif "Public") Enregistrer, enregistrer sous et enregistrer toute la gestion des commandes pour un éditeur standard

 Ce processus est détaillé dans les étapes suivantes :

1. Lorsque les commandes **Enregistrer** et **Enregistrer sous** sont sélectionnées, l’environnement utilise le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> pour déterminer la fenêtre de document active et, par conséquent, les éléments à enregistrer. Une fois que la fenêtre de document active est connue, l’environnement recherche le pointeur de hiérarchie et l’identificateur d’élément (itemID) du document dans la table de document en cours d’exécution. Pour plus d’informations, consultez exécution de la [table des documents](../../extensibility/internals/running-document-table.md).

    Lorsque la commande **enregistrer tout** est sélectionnée, l’environnement utilise les informations contenues dans la table de document en cours d’exécution pour compiler la liste de tous les éléments à enregistrer.

2. Lorsque la solution reçoit un appel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>, elle itère au sein de l’ensemble d’éléments sélectionnés (autrement dit, les sélections multiples exposées par le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>).

3. Sur chaque élément de la sélection, la solution utilise le pointeur de hiérarchie pour appeler la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> pour déterminer si la commande de menu **Enregistrer** doit être activée. Si un ou plusieurs éléments sont modifiés, la commande **Enregistrer** est activée. Si la hiérarchie utilise un éditeur standard, la hiérarchie délègue l’interrogation de l’état incorrect à l’éditeur en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. Sur chaque élément sélectionné qui est modifié, la solution utilise le pointeur de hiérarchie pour appeler la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> sur les hiérarchies appropriées.

    Il est courant pour la hiérarchie d’utiliser un éditeur standard pour modifier le document. Dans ce cas, l’objet de données de document pour cet éditeur doit prendre en charge l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>. Lors de la réception de l’appel de méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>, le projet doit informer l’éditeur que le document est enregistré en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> sur l’objet de données de document. L’éditeur peut autoriser l’environnement à gérer la boîte de dialogue **Enregistrer sous** en appelant `Query Service` pour l’interface <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>. Cela retourne un pointeur vers l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>. L’éditeur doit ensuite appeler la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>, en passant un pointeur vers l’implémentation <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> de l’éditeur au moyen du paramètre `pPersistFile`. L’environnement effectue ensuite l’opération d’enregistrement et fournit la boîte de dialogue **Enregistrer sous** de l’éditeur. L’environnement appelle ensuite l’éditeur avec <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.

5. Si l’utilisateur tente d’enregistrer un document sans titre (autrement dit, un document précédemment non enregistré), une commande Enregistrer sous est exécutée.

6. Pour la commande Enregistrer sous, l’environnement affiche la boîte de dialogue Enregistrer sous, qui invite l’utilisateur à entrer un nom de fichier.

    Si le nom du fichier a changé, la hiérarchie est chargée de mettre à jour les informations mises en cache du frame de document en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument).

   Si la commande **Enregistrer sous** déplace l’emplacement du document et que la hiérarchie est sensible à l’emplacement du document, la hiérarchie est chargée de transmettre la propriété de la fenêtre de document ouverte à une autre hiérarchie. Par exemple, cela se produit si le projet suit si le fichier est un fichier interne ou externe (fichier divers) par rapport au projet. Utilisez la procédure suivante pour modifier la propriété d’un fichier dans le projet fichiers divers.

## <a name="changing-file-ownership"></a>Modification de la propriété du fichier

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Pour modifier la propriété du fichier pour le projet fichiers divers

1. Service de requête pour l’interface <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>.

     Un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> est retourné.

2. Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) pour transférer le document vers la nouvelle hiérarchie. La hiérarchie effectuant la commande Enregistrer sous appelle cette méthode.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)