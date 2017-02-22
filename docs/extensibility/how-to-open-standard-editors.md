---
title: "Comment : ouvrir les &#233;diteurs Standard | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), ouverture"
  - "projets (Visual Studio SDK), ouverture des éditeurs standards"
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Comment : ouvrir les &#233;diteurs Standard
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous ouvrez un éditeur standard, vous laissez l'IDE déterminer un éditeur standard pour un type de fichier indiqué, au lieu de spécifier un éditeur spécifique aux projets pour le fichier.  
  
 Effectuez la procédure suivante pour implémenter la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> .  Cela ouvre un fichier projet dans un éditeur standard.  
  
### Pour implémenter la méthode d'OpenItem avec un éditeur standard  
  
1.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> \(`RDT_EditLock`\) pour déterminer si le fichier objet de données du document est déjà ouvert.  
  
2.  Si le fichier est déjà ouvert, reblanchissez le fichier en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> , en spécifiant une valeur d' `IDO_ActivateIfOpen` pour le paramètre d' `grfIDO` .  
  
     Si le fichier est ouvert et le document est détenu par un projet différent du projet appelant, votre projet accepte un avertissement indiquant que l'éditeur est ouvert est d'un autre projet.  La fenêtre de fichier est ensuite apprêtée.  
  
3.  Si le document n'est pas ouvert ou non dans le tableau en cours de exécution de document, appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> \(`OSE_ChooseBestStdEditor`\) pour ouvrir un éditeur standard pour le fichier.  
  
     Lorsque vous appelez la méthode, l'IDE exécute les tâches suivantes :  
  
    1.  L'IDE analyse la sous\-clé d'éditeurs guidEditorType {} \/Extensions dans le Registre pour déterminer quel éditeur peut ouvrir le fichier et a la priorité la plus élevée pour ce faire.  
  
    2.  Après que l'IDE a déterminé quel éditeur peut ouvrir le fichier, l'IDE appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  L'implémentation de l'éditeur de cette méthode retourne les informations requises pour que l'IDE appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> et de pour naviguer jusqu ' à le document récemment ouvert.  
  
    3.  Enfin, l'IDE charge le document à l'aide de l'interface habituelle de persistance, telle qu' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Si l'IDE précédemment a déterminé que la hiérarchie ou l'élément de hiérarchie est disponible, l'IDE appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> sur le projet d'obtenir un pointeur d' <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> de contexte de niveau projet à retourner dans avec l'appel de méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> .  
  
4.  Retournez plutôt un pointeur d' <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> à l'IDE lorsque l'IDE appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> sur votre projet si vous souhaitez quitter le contexte get de l'éditeur de votre projet.  
  
     Exécuter cette étape permet de les services supplémentaires d'offrir de projet dans l'éditeur.  
  
     Si l'objet de vue du document ou de document a été correctement trouve dans un frame de fenêtre, l'objet est initialisé avec ses données en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Comment : ouvrir les éditeurs spécifiques au projet](../extensibility/how-to-open-project-specific-editors.md)   
 [Comment : ouvrir des éditeurs pour les Documents ouverts](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Afficher les fichiers à l'aide de la commande Ouvrir un fichier](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)