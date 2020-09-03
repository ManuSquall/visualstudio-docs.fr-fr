---
title: 'Procédure : ouvrir des éditeurs standard | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c12e831654e7e138289d33b6e6f0409328e22c8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905788"
---
# <a name="how-to-open-standard-editors"></a>Procédure : ouvrir des éditeurs standard
Lorsque vous ouvrez un éditeur standard, vous laissez l’IDE déterminer un éditeur standard pour un type de fichier désigné, au lieu de spécifier un éditeur spécifique au projet pour le fichier.

 Effectuez la procédure suivante pour implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> méthode. Cela permet d’ouvrir un fichier projet dans un éditeur standard.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Pour implémenter la méthode OpenItem avec un éditeur standard

1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> ( `RDT_EditLock` ) pour déterminer si le fichier d’objet de données de document est déjà ouvert.

2. Si le fichier est déjà ouvert, réaffichez le fichier en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> méthode, en spécifiant la valeur `IDO_ActivateIfOpen` pour le `grfIDO` paramètre.

     Si le fichier est ouvert et que le document est détenu par un autre projet que le projet appelant, votre projet reçoit un avertissement indiquant que l’éditeur est ouvert à partir d’un autre projet. La fenêtre de fichier est alors exposée.

3. Si le document n’est pas ouvert ou pas dans la table de document en cours d’exécution, appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode ( `OSE_ChooseBestStdEditor` ) pour ouvrir un éditeur standard pour le fichier.

     Lorsque vous appelez la méthode, l’IDE effectue les tâches suivantes :

    1. L’IDE analyse la sous-clé Editers/{guidEditorType}/extensions dans le registre pour déterminer quel éditeur peut ouvrir le fichier et a la priorité la plus élevée pour ce faire.

    2. Une fois que l’IDE a déterminé quel éditeur peut ouvrir le fichier, l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . L’implémentation de cette méthode de l’éditeur retourne des informations qui sont requises pour que l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> et place le document qui vient d’être ouvert.

    3. Enfin, l’IDE charge le document à l’aide de l’interface de persistance habituelle, telle que <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .

    4. Si l’IDE a déterminé précédemment que l’élément de hiérarchie ou de hiérarchie est disponible, l’IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> méthode sur le projet pour obtenir un pointeur de contexte au niveau <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> du projet à renvoyer avec l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> appel de méthode.

4. Retournez un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> pointeur vers l’IDE lorsque l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> sur votre projet si vous souhaitez autoriser l’éditeur à obtenir le contexte de votre projet.

     L’exécution de cette étape permet au projet d’offrir des services supplémentaires à l’éditeur.

     Si la vue de document ou l’objet de vue de document a été correctement installé dans un frame de fenêtre, l’objet est initialisé avec ses données en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> .

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)
- [Comment : ouvrir des éditeurs spécifiques à un projet](../extensibility/how-to-open-project-specific-editors.md)
- [Procédure : ouvrir les éditeurs pour les documents ouverts](../extensibility/how-to-open-editors-for-open-documents.md)
- [Afficher les fichiers à l’aide de la commande ouvrir un fichier](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
