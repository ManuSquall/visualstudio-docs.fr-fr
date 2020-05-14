---
title: Enregistrement d’un document standard (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705549"
---
# <a name="saving-a-standard-document"></a>Enregistrement d’un document standard
L’environnement gère les commandes Save, Save As et Save All. Lorsqu’un utilisateur sélectionne **Enregistrer,** **enregistrer comme**, ou **enregistrer tous** dans le menu **Fichier** ou ferme la solution, résultant en un **Save All**, le processus suivant se produit.

 ![Rédacteur standard](../../extensibility/internals/media/public.gif "Public") Enregistrer, enregistrer as et enregistrer toute la manipulation de commande pour un éditeur standard

 Ce processus est détaillé dans les étapes suivantes :

1. Lorsque les commandes **Enregistrer** et enregistrer au fur <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> et à **mesure** sont sélectionnées, l’environnement utilise le service pour déterminer la fenêtre de document active et donc quels éléments doivent être enregistrés. Une fois que la fenêtre de document active est connue, l’environnement trouve le pointeur de hiérarchie et l’identifiant d’élément (itemID) pour le document dans la table de document en cours d’exécution. Pour plus d’informations, voir [Tableau des documents d’exécution](../../extensibility/internals/running-document-table.md).

    Lorsque la commande **Save All** est sélectionnée, l’environnement utilise les informations contenues dans le tableau de document en cours d’exécution pour compiler la liste de tous les éléments à enregistrer.

2. Lorsque la solution <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> reçoit un appel, elle s’isère à travers l’ensemble <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> d’éléments sélectionnés (c’est-à-dire les sélections multiples exposées par le service).

3. Sur chaque élément de la sélection, la solution <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> utilise le pointeur de hiérarchie pour appeler la méthode pour déterminer si la commande de menu **Enregistrer** doit être activée. Si un ou plusieurs articles sont sales, la commande **Save** est activée. Si la hiérarchie utilise un éditeur standard, alors la hiérarchie délègue <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> le statut sale à l’éditeur en appelant la méthode.

4. Sur chaque élément sélectionné qui est sale, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> solution utilise le pointeur de hiérarchie pour appeler la méthode sur les hiérarchies appropriées.

    Il est courant pour la hiérarchie d’utiliser un éditeur standard pour modifier le document. Dans ce cas, l’objet de données <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> de document pour cet éditeur doit prendre en charge l’interface. Lors de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> la réception de l’appel de méthode, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> projet doit informer l’éditeur que le document est enregistré en appelant la méthode sur l’objet de données de document. L’éditeur peut permettre à l’environnement de gérer `Query Service` la <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> boîte de dialogue **Save As,** en appelant à l’interface. Cela renvoie un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> pointeur à l’interface. L’éditeur doit <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> alors appeler la méthode, en <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> passant un `pPersistFile` pointeur à la mise en œuvre de l’éditeur au moyen du paramètre. L’environnement effectue ensuite l’opération Save et fournit la boîte de dialogue **Save As** pour l’éditeur. L’environnement rappelle ensuite à <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>l’éditeur avec .

5. Si l’utilisateur tente d’enregistrer un document sans titre (c’est-à-dire un document précédemment nonavé), alors une commande Save As est effectivement effectuée.

6. Pour la commande Save As, l’environnement affiche la boîte de dialogue Save As, incitant l’utilisateur à obtenir un nom de fichier.

    Si le nom du fichier a changé, alors la hiérarchie est responsable de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>la mise à jour des informations mises en cache du cadre du document en appelant (VSFPROPID_MkDocument).

   Si la commande **Save As** déplace l’emplacement du document, et que la hiérarchie est sensible à l’emplacement du document, la hiérarchie est chargée de céder la propriété de la fenêtre de document ouverte à une autre hiérarchie. Par exemple, cela se produit si le projet suit si le fichier est un fichier interne ou externe (Fichier divers) par rapport au projet. Utilisez la procédure suivante pour changer la propriété d’un fichier au projet Divers Files.

## <a name="changing-file-ownership"></a>Modification de la propriété du fichier

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Pour changer la propriété du fichier au projet Divers Files

1. Service de requête <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> pour l’interface.

     Un pointeur à <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> est retourné.

2. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> la`pszMkDocumentNew` `punkWindowFrame`méthode ( , ) pour transférer le document à la nouvelle hiérarchie. La hiérarchie exécutant le Save As command appelle cette méthode.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)
