---
title: "Enregistrement d&#39;un Document Standard | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), l'enregistrement de documents standards"
  - "projets (Visual Studio SDK), l'enregistrement de documents standards"
  - "persistance, l'enregistrement de documents standards"
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Enregistrement d&#39;un Document Standard
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les handles d'environnement de la sauvegarde, enregistrez comme, et enregistrent toutes les commandes.  Lorsqu'un utilisateur sélectionne **Enregistrer**, **Enregistrer sous**, ou **Enregistrer tout** dans le menu de **Fichier** ou se ferme la solution, ce qui provoque **Enregistrer tout**, le processus suivant se produit.  
  
 ![Éditeur standard](~/docs/extensibility/internals/media/public.gif "Public")  
Enregistrez, enregistrer sous, puis enregistrez toutes la gestion de commande pour un éditeur standard  
  
 Ce processus est indiqué dans les étapes suivantes :  
  
1.  Lorsque les commandes d' **Enregistrer** et d' **Enregistrer sous** sont sélectionnées, l'environnement utilise le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> pour déterminer la fenêtre de document actif et ainsi les éléments doivent être stockés.  Une fois que la fenêtre de document actif est connue, l'environnement recherche l'identificateur de pointeur et d'éléments de hiérarchie \(itemID\) pour le document dans le tableau en cours de exécution de document.  Pour plus d'informations, consultez [Table de Document en cours d’exécution](../../extensibility/internals/running-document-table.md).  
  
     Lorsque la commande d' **Enregistrer tout** est sélectionnée, l'environnement utilise les informations contenues dans la table en cours de exécution de document pour compiler la liste de tous les éléments à enregistrer.  
  
2.  Lorsque la solution reçoit un appel d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , il itère au sein de l'ensemble d'éléments sélectionnés \(autrement dit, les sélections multiples exposées par le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> \).  
  
3.  Sur chaque élément dans la sélection, la solution utilise le pointeur de la hiérarchie pour appeler la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> pour déterminer si la commande de menu d' **Save** doit être activée.  Si un ou plusieurs éléments sont modifiés, l'ordre d' **Save** est activée.  Si la hiérarchie utilise un éditeur standard, la hiérarchie d'interroger l'état modifié dans l'éditeur en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> .  
  
4.  Sur chaque élément sélectionné modifiée, la solution utilise le pointeur de la hiérarchie pour appeler la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> sur les hiérarchies appropriées.  
  
     Il est courant de la hiérarchie utilise un éditeur standard pour modifier le document.  Dans ce cas, l'objet de données du document pour cet éditeur doit prendre en charge l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .  En recevant l'appel de méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> , le projet doit informer l'éditeur que le document est enregistré en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> sur l'objet de données du document.  l'éditeur peut permettre à l'environnement pour gérer la boîte de dialogue d' **Enregistrer sous** , en appelant `Query Service` pour l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> .  Cela retourne un pointeur vers l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> .  L'éditeur doit ensuite appeler la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> , en passant un pointeur vers l'implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> de l'éditeur par l'intermédiaire de le paramètre d' `pPersistFile` .  L'environnement au moment exécute l'opération d'enregistrement et fournit la boîte de dialogue d' **Enregistrer sous** pour l'éditeur.  Les appels d'environnement puis vers l'éditeur avec <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Si l'utilisateur tente d'enregistrer un document sans titre \(autrement dit, un document précédemment non enregistré\), une commande enregistrer sous est réellement exécutée.  
  
6.  Pour la commande enregistrer sous, l'environnement affiche la boîte de dialogue enregistrer sous, invitant l'utilisateur à entrer un nom de fichier.  
  
     Si le nom du fichier a changé, la hiérarchie est responsable de la mise à jour les informations mises en cache du frame de document en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>\(VSFPROPID\_MkDocument\).  
  
 Si l'ordre des **Enregistrer sous** déplace l'emplacement du document, et la hiérarchie ne respecte pas la localisation des documents, la hiérarchie est responsable de la remise en dehors de la propriété de la fenêtre de document ouvert à une autre hiérarchie.  Par exemple, cela se produit si le projet suit si le fichier est un fichier interne ou externe \(fichier divers\) liés au projet.  Utilisez la procédure suivante pour modifier la propriété d'un fichier au projet Fichiers divers.  
  
## Modifier la propriété du fichier  
  
#### À la propriété du fichier spécifique au projet Fichiers divers  
  
1.  service de requête pour l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> .  
  
     Un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> est retourné.  
  
2.  appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> \(`pszMkDocumentNew`, `punkWindowFrame`\) pour transférer le document à la nouvelle hiérarchie.  La hiérarchie exécutant la commande enregistrer sous appelle cette méthode.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)