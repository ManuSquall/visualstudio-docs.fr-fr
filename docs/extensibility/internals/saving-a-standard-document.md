---
title: Enregistrement d’un Document Standard | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 460b948ea7b5bace1b91143d46a4ca2f4c823608
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859149"
---
# <a name="saving-a-standard-document"></a>Enregistrement d’un document standard
L’environnement gère l’enregistrer, enregistrer sous et enregistrer toutes les commandes. Lorsqu’un utilisateur sélectionne **enregistrer**, **enregistrer en tant que**, ou **Enregistrer tout** à partir de la **fichier** menu ou ferme la solution, ce qui entraîne un  **Enregistrer tous les**, le processus suivant se produit.

 ![Éditeur standard](../../extensibility/internals/media/public.gif "Public") enregistrer, enregistrer sous et enregistrer tout gestion des commandes pour un éditeur standard

 Ce processus est détaillé dans les étapes suivantes :

1. Lorsque le **enregistrer** et **enregistrer en tant que** commandes sont activées, l’environnement utilise le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> pour déterminer la fenêtre du document de service et par conséquent, les éléments qui doivent être enregistrés. Une fois que la fenêtre de document actif est connue, l’environnement recherche le pointeur de la hiérarchie et l’identificateur de l’élément (itemID) pour le document dans la table de document en cours d’exécution. Pour plus d’informations, consultez [Table de Document en cours d’exécution](../../extensibility/internals/running-document-table.md).

    Lorsque le **Enregistrer tout** commande est sélectionnée, l’environnement utilise les informations dans la table de document en cours d’exécution pour compiler la liste de tous les éléments à enregistrer.

2. Lorsque la solution reçoit un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> appel, il itère l’ensemble des éléments sélectionnés (autrement dit, les sélections multiples exposées par le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service).

3. Sur chaque élément de la sélection, la solution utilise le pointeur de la hiérarchie pour appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> méthode pour déterminer si le **enregistrer** commande de menu doit être activée. Si un ou plusieurs éléments sont modifiés, puis le **enregistrer** commande est activée. Si la hiérarchie utilise un éditeur standard, les délégués de hiérarchie recherchant dirty état à l’éditeur en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> (méthode).

4. Sur chaque élément sélectionné a été modifié, la solution utilise le pointeur de la hiérarchie pour appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> (méthode) sur les hiérarchies appropriés.

    Il est courant pour la hiérarchie à utiliser un éditeur standard pour modifier le document. Dans ce cas, les données du document d’objet pour cet éditeur doit prendre en charge la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interface. À la réception du <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> appel de méthode, le projet doit informer l’éditeur de l’enregistrement du document en cours en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> méthode sur l’objet de données de document. L’éditeur peut permettre à l’environnement gérer la **enregistrer en tant que** boîte de dialogue, en appelant `Query Service` pour le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interface. Cela retourne un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface. L’éditeur doit ensuite appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> méthode, en passant un pointeur vers le mot du rédacteur <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> mise en œuvre par le biais de la `pPersistFile` paramètre. L’environnement, puis effectue l’opération d’enregistrement et fournit le **Enregistrer sous** boîte de dialogue de l’éditeur. L’environnement rappelle ensuite à l’éditeur avec <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.

5. Si l’utilisateur tente d’enregistrer un document sans titre (autrement dit, un document non enregistré précédemment), puis une commande Enregistrer sous réellement exécutée.

6. Pour la commande Enregistrer sous, l’environnement affiche la boîte de dialogue Enregistrer sous, inviter l’utilisateur à un nom de fichier.

    Si le nom du fichier a changé, la hiérarchie est responsable de la mise à jour le frame de document informations mises en cache en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).

   Si le **Enregistrer sous** commande déplace l’emplacement du document, la hiérarchie est sensible à l’emplacement du document, puis la hiérarchie est responsable de la remise de la propriété de la fenêtre de document vers une autre hiérarchie. Par exemple, cela se produit si le projet détermine si le fichier est un fichier interne ou externe (fichier divers) en relation avec le projet. Utilisez la procédure suivante pour modifier le propriétaire d’un fichier pour le projet fichiers divers.

## <a name="changing-file-ownership"></a>Modification de la propriété de fichier

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Pour modifier la propriété de fichier pour le projet fichiers divers

1. Interroger le Service pour le <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interface.

     Un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> est retourné.

2. Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) méthode pour transférer le document vers la nouvelle hiérarchie. La hiérarchie de l’exécution de la commande Enregistrer sous appelle cette méthode.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)