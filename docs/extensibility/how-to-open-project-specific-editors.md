---
title: "Comment : ouvrir les &#233;diteurs sp&#233;cifiques au projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "types de projets, ouvrir un éditeur spécifique au projet"
  - "éditeurs (Visual Studio SDK), ouverture des éditeurs de spécifiques au projet"
  - "ouvrir les dossiers de projets (Visual Studio SDK),"
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment : ouvrir les &#233;diteurs sp&#233;cifiques au projet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si un fichier d'élément ouvert par un projet est intrinsèquement lié à l'éditeur particulier pour ce projet, le projet doit ouvrir le fichier à l'aide d'un éditeur spécifique au projet.  Le fichier ne peut pas être délégué vers le bas au mécanisme de l'IDE pour sélectionner un éditeur.  Par exemple, au lieu d'utiliser un éditeur de bitmaps standard, vous pouvez utiliser cette option de l'éditeur spécifique au projet de spécifier un éditeur de bitmaps spécifique qui identifie les informations dans le fichier propre à votre projet.  
  
 L'IDE appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> lorsqu'il détermine qu'un fichier doit être ouvert par un projet spécifique.  Pour plus d'informations, consultez [Afficher les fichiers à l'aide de la commande Ouvrir un fichier](../extensibility/internals/displaying-files-by-using-the-open-file-command.md).  Suivez les directives suivantes pour implémenter la méthode d' `OpenItem` pour que votre projet ouvrez un fichier à l'aide d'un éditeur spécifique au projet.  
  
### Pour implémenter la méthode d'OpenItem avec un éditeur spécifique au projet  
  
1.  Appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> \(RDT\_EditLock\) pour déterminer si le fichier \(objet de données du document\) est déjà ouvert.  
  
    > [!NOTE]
    >  Pour plus d'informations sur les objets de vue de données et le fichier de document, consultez [Données de documents et affichage de documents dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  si le fichier est déjà ouvert, reblanchissez le fichier en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> et en spécifiant une valeur d'IDO\_ActivateIfOpen pour le paramètre d' `grfIDO` .  
  
     Si le fichier est ouvert et le document est détenu par un projet autre que le projet appelant, un avertissement s'affiche à l'utilisateur que l'éditeur est ouvert est d'un autre projet.  La fenêtre de fichier est ensuite apprêtée.  
  
3.  Si votre mémoire tampon de texte \(objet de données du document\) est déjà ouverte et vous souhaitez attacher une autre vue à elle, vous êtes chargé de raccorder en haut de cette vue.  L'approche recommandée à instancier une vue \(objet de vue du document\) du projet, est la suivante :  
  
    1.  Appelez `QueryService` au service d' <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> pour obtenir un pointeur vers l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> .  
  
    2.  appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> pour créer une instance de la classe d'affichage de document.  
  
4.  Appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> , en spécifiant votre objet de vue du document.  
  
     Cette méthode est installé dans l'objet de vue du document dans une fenêtre de document.  
  
5.  Exécutez les appels adaptés à <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> ou aux méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> .  
  
     À ce stade, la vue doit être complètement initialisée et prête à être ouverte.  
  
6.  Appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> pour afficher et ouvrir la vue.  
  
## Voir aussi  
 [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Comment : ouvrir les éditeurs Standard](../extensibility/how-to-open-standard-editors.md)   
 [Comment : ouvrir des éditeurs pour les Documents ouverts](../extensibility/how-to-open-editors-for-open-documents.md)