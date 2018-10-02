---
title: 'Comment : ouvrir des éditeurs spécifiques du projet | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a529237b8aa77fbb909278d5a7accd2e9a45265
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508653"
---
# <a name="how-to-open-project-specific-editors"></a>Comment : ouvrir des éditeurs spécifiques du projet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : ouvrir éditeurs spécifiques du projet](https://docs.microsoft.com/visualstudio/extensibility/how-to-open-project-specific-editors).  
  
Si un fichier de l’élément en cours d’ouverture par un projet est intrinsèquement lié à l’éditeur pour ce projet particulier, le projet doit ouvrir le fichier à l’aide d’un éditeur spécifique au projet. Le fichier ne peut pas être délégué au mécanisme de l’IDE pour la sélection d’un éditeur. Par exemple, au lieu d’utiliser un éditeur de bitmaps standard, vous pouvez utiliser cette option d’éditeur spécifiques au projet pour spécifier un éditeur de bitmaps spécifique qui reconnaît les informations contenues dans le fichier qui est unique à votre projet.  
  
 Les appels de l’IDE le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> méthode lorsqu’il détermine qu’un fichier doit être ouvert par un projet spécifique. Pour plus d’informations, consultez [affichage des fichiers à l’aide de la commande fichier ouvrir](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Utilisez les instructions suivantes pour implémenter le `OpenItem` méthode pour que votre projet à ouvrir un fichier à l’aide d’un éditeur spécifique au projet.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Pour implémenter la méthode OpenItem avec un éditeur spécifique au projet  
  
1.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> (méthode) (RDT_EditLock) pour déterminer si le fichier (objet de données de document) est déjà ouvert.  
  
    > [!NOTE]
    >  Pour plus d’informations sur les données de document et les objets de vue de document, consultez [des données du Document et affichage de documents dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Si le fichier est déjà ouvert, resurface le fichier en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> méthode et en spécifiant une valeur de IDO_ActivateIfOpen pour le `grfIDO` paramètre.  
  
     Si le fichier est ouvert et que le document est détenu par un projet autre que le projet appelant, un avertissement s’affichera à l’utilisateur qui est de l’éditeur en cours d’ouverture d’un autre projet. La fenêtre de fichier est ensuite présentée.  
  
3.  Si votre mémoire tampon de texte (objet de données de document) est déjà ouvert et vous souhaitez attacher une autre vue à celui-ci, vous êtes responsable de raccorder à cette vue. L’approche recommandée pour l’instanciation d’une vue (objet de vue de document) à partir du projet, est la suivante :  
  
    1.  Appelez `QueryService` sur le <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> service afin d’obtenir un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interface.  
  
    2.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> méthode pour créer une instance de la classe de vue de document.  
  
4.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> méthode, en spécifiant votre objet de vue de document.  
  
     Cette méthode sites l’objet de vue de document dans une fenêtre de document.  
  
5.  Effectuer les appels appropriés aux soit le <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> méthodes.  
  
     À ce stade, la vue doit être entièrement initialisé et prêt à être ouvert.  
  
6.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> méthode pour afficher et ouvrir la vue.  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Comment : ouvrir des éditeurs Standard](../extensibility/how-to-open-standard-editors.md)   
 [Guide pratique pour ouvrir des éditeurs pour les documents ouverts](../extensibility/how-to-open-editors-for-open-documents.md)

