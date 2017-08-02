---
title: "Enregistrement d&#39;un Document personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistance, l'enregistrement de documents personnalisés"
  - "projets (Visual Studio SDK), l'enregistrement de documents personnalisés"
  - "éditeurs (Visual Studio SDK), l'enregistrement de documents personnalisés"
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Enregistrement d&#39;un Document personnalis&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

les handles d'environnement **Save**, **Save As**, et commandes d' **Save All** .  Lorsqu'un utilisateur clique sur **Enregistrer**, **Enregistrer sous**, **ou enregistrer tout** dans le menu de **Fichier** ou fermez la solution, ce qui entraînerait une sauvegarde toute, le processus suivant se produit.  
  
 ![Enregistrer l'éditeur du client](~/docs/extensibility/internals/media/private.gif "Private")  
Enregistrez, enregistrer sous, puis enregistrez toutes la gestion de contrôle pour un éditeur personnalisé  
  
 Ce processus est indiqué dans les étapes suivantes :  
  
1.  Pour les commandes des **Enregistrer** et d' **Enregistrer sous** , l'environnement utilise le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> pour déterminer la fenêtre de document actif et ainsi les éléments doivent être stockés.  Une fois que la fenêtre de document actif est connue, l'environnement recherche l'identificateur de pointeur et d'éléments de hiérarchie \(itemID\) pour le document dans le tableau en cours de exécution de document.  Pour plus d'informations, consultez [Table de Document en cours d’exécution](../../extensibility/internals/running-document-table.md).  
  
     Pour l'enregistrement toute la commande, l'environnement utilise les informations contenues dans la table en cours de exécution de document pour compiler la liste de tous les éléments à enregistrer.  
  
2.  Lorsque la solution reçoit un appel d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , il itère au sein de l'ensemble d'éléments sélectionnés \(autrement dit, les sélections multiples exposées par le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> \).  
  
3.  Sur chaque élément dans la sélection, la solution utilise le pointeur de la hiérarchie pour appeler la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> pour déterminer si la commande de menu d'enregistrement doit être activée.  Si un ou plusieurs éléments sont modifiés, la commande enregistrer est activée.  Si la hiérarchie utilise un éditeur standard, la hiérarchie d'interroger l'état modifié dans l'éditeur en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> .  
  
4.  Sur chaque élément sélectionné modifiée, la solution utilise le pointeur de la hiérarchie pour appeler la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> sur les hiérarchies appropriées.  
  
     Dans le cas d'un éditeur personnalisé, la communication entre l'objet de données du document et le projet est privée.  Par conséquent, tous les problèmes spéciaux de persistance sont gérés entre ces deux objets.  
  
    > [!NOTE]
    >  Si vous implémentez votre propre persistance, veillez à appeler la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> pour gagner du temps.  Cette méthode vérifie pour vous assurer qu'il est possible d'enregistrer le fichier \(par exemple, le fichier n'est pas en lecture seule\).  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)