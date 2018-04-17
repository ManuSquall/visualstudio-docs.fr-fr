---
title: 'Comment : ouvrir les éditeurs spécifiques au projet | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae2e634d36c13632619d01cc97d5726dc5576819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-open-project-specific-editors"></a>Comment : ouvrir les éditeurs spécifiques au projet
Si un fichier d’élément en cours d’ouverture par un projet est intrinsèquement lié à l’éditeur particulière pour ce projet, le projet doit ouvrir le fichier à l’aide d’un éditeur spécifique au projet. Le fichier ne peut pas être délégué au mécanisme de l’IDE pour la sélection d’un éditeur. Par exemple, au lieu d’utiliser un éditeur de bitmaps standard, vous pouvez utiliser cette option d’éditeur spécifiques au projet pour spécifier un éditeur spécifique de bitmap qui reconnaît les informations dans le fichier qui est unique à votre projet.  
  
 Les appels de l’IDE le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> méthode lorsqu’il détermine qu’un fichier doit être ouvert par un projet spécifique. Pour plus d’informations, consultez [affichage des fichiers à l’aide de la commande fichier ouvrir](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Utilisez les instructions suivantes pour implémenter le `OpenItem` méthode à votre projet est ouvert un fichier à l’aide d’un éditeur spécifique au projet.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Pour implémenter la méthode OpenItem avec un éditeur spécifique au projet  
  
1.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> (méthode) (RDT_EditLock) pour déterminer si le fichier (objet de données de document) est déjà ouvert.  
  
    > [!NOTE]
    >  Pour plus d’informations sur les données du document et les objets de vue de document, consultez [des données du Document et affichage de documents dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Si le fichier est déjà ouvert, resurface le fichier en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> méthode et en spécifiant une valeur de IDO_ActivateIfOpen pour la `grfIDO` paramètre.  
  
     Si le fichier est ouvert et que le document appartient à un projet autre que le projet appelant, un avertissement s’affichera à l’utilisateur qui est de l’éditeur est ouvert à partir d’un autre projet. La fenêtre de fichier puis apparaissent.  
  
3.  Si votre mémoire tampon de texte (objet de données de document) est déjà ouvert et que vous souhaitez attacher une autre vue, vous êtes responsable de la raccorder à cette vue. Il est recommandé à l’instanciation d’une vue (objet de vue de document) à partir du projet, comme suit :  
  
    1.  Appelez `QueryService` sur la <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> service pour obtenir un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interface.  
  
    2.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> méthode pour créer une instance de la classe de vue de document.  
  
4.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> méthode, en spécifiant votre objet de vue de document.  
  
     Cette méthode sites à l’objet de vue de document dans une fenêtre de document.  
  
5.  Effectuer les appels appropriés aux soit le <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> méthodes.  
  
     À ce stade, la vue doit être entièrement initialisé et prêt à ouvrir.  
  
6.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> méthode pour afficher et ouvrir la vue.  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Comment : ouvrir les éditeurs Standard](../extensibility/how-to-open-standard-editors.md)   
 [Guide pratique pour ouvrir des éditeurs pour les documents ouverts](../extensibility/how-to-open-editors-for-open-documents.md)