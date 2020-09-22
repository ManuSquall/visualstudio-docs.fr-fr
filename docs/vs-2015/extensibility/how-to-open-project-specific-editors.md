---
title: 'Comment : ouvrir des éditeurs spécifiques à un projet | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2439a07f63b8da854ca8dc331d26e30f49503257
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840113"
---
# <a name="how-to-open-project-specific-editors"></a>Guide pratique pour ouvrir des éditeurs spécifiques à un projet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si un fichier d’élément qui est ouvert par un projet est lié intrinsèquement à l’éditeur spécifique de ce projet, le projet doit ouvrir le fichier à l’aide d’un éditeur spécifique au projet. Le fichier ne peut pas être délégué au mécanisme de l’IDE pour sélectionner un éditeur. Par exemple, au lieu d’utiliser un éditeur de bitmaps standard, vous pouvez utiliser cette option de l’éditeur spécifique au projet pour spécifier un éditeur de bitmaps spécifique qui reconnaît les informations du fichier qui sont uniques à votre projet.  
  
 L’IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> méthode lorsqu’il détermine qu’un fichier doit être ouvert par un projet spécifique. Pour plus d’informations, consultez [affichage de fichiers à l’aide de la commande ouvrir un fichier](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Utilisez les instructions suivantes pour implémenter la `OpenItem` méthode afin que votre projet ouvre un fichier à l’aide d’un éditeur spécifique au projet.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Pour implémenter la méthode OpenItem avec un éditeur spécifique au projet  
  
1. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> méthode (RDT_EditLock) pour déterminer si le fichier (objet de données de document) est déjà ouvert.  
  
    > [!NOTE]
    > Pour plus d’informations sur les données de document et les objets de vue de document, consultez [données de document et vue de document dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2. Si le fichier est déjà ouvert, réaffichez le fichier en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> méthode et en spécifiant la valeur IDO_ActivateIfOpen pour le `grfIDO` paramètre.  
  
     Si le fichier est ouvert et que le document appartient à un projet autre que le projet appelant, un avertissement s’affiche pour l’utilisateur que l’éditeur est ouvert à partir d’un autre projet. La fenêtre de fichier est alors exposée.  
  
3. Si votre mémoire tampon de texte (objet de données de document) est déjà ouverte et que vous souhaitez y attacher une autre vue, vous êtes responsable du raccordement de cette vue. L’approche recommandée pour instancier une vue (objet de vue de document) à partir du projet est la suivante :  
  
    1. Appelez `QueryService` sur le <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> service pour obtenir un pointeur vers l' <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interface.  
  
    2. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> méthode pour créer une instance de la classe d’affichage de document.  
  
4. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> méthode, en spécifiant votre objet de vue de document.  
  
     Cette méthode site l’objet de vue de document dans une fenêtre de document.  
  
5. Effectuez les appels appropriés aux <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> méthodes ou.  
  
     À ce stade, la vue doit être entièrement initialisée et prête à être ouverte.  
  
6. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> méthode pour afficher et ouvrir la vue.  
  
## <a name="see-also"></a>Voir aussi  
 [Ouverture et enregistrement d’éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procédure : ouvrir des éditeurs standard](../extensibility/how-to-open-standard-editors.md)   
 [Guide pratique pour ouvrir des éditeurs pour les documents ouverts](../extensibility/how-to-open-editors-for-open-documents.md)
