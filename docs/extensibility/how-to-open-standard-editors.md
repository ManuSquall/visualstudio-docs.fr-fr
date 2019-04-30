---
title: 'Procédure : Ouvrir des éditeurs Standard | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f34a239628c3ed9e8bccaa8590cb22100d7d290f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862912"
---
# <a name="how-to-open-standard-editors"></a>Procédure : Éditeurs standards Open
Lorsque vous ouvrez un éditeur standard, vous laisser l’IDE détermine un éditeur standard pour un type de fichier désigné, au lieu de spécifier un éditeur spécifique au projet pour le fichier.

 Effectuez la procédure suivante pour implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> (méthode). Un fichier projet s’ouvre dans un éditeur standard.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Pour implémenter la méthode OpenItem avec un éditeur standard

1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) pour déterminer si le fichier d’objet de données document est déjà ouvert.

2. Si le fichier est déjà ouvert, resurface le fichier en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> méthode, en spécifiant une valeur de `IDO_ActivateIfOpen` pour le `grfIDO` paramètre.

     Si le fichier est ouvert et que le document appartient à un projet différent de celui du projet appelant, votre projet reçoit un avertissement indiquant que l’éditeur en cours d’ouverture est d’un autre projet. La fenêtre de fichier est ensuite présentée.

3. Si le document n’est pas ouvert ou non dans la table de document en cours d’exécution, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> (méthode) (`OSE_ChooseBestStdEditor`) pour ouvrir un éditeur standard pour le fichier.

     Lorsque vous appelez la méthode, l’IDE effectue les tâches suivantes :

    1. L’IDE analyse les éditeurs / {guidEditorType} / sous-clé Extensions dans le Registre pour déterminer l’éditeur peut ouvrir le fichier et a la priorité la plus élevée pour effectuer cette opération.

    2. Une fois que l’IDE a déterminé l’éditeur que vous pouvez ouvrir le fichier, l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Implémentation de l’éditeur de cette méthode retourne des informations qui est requises pour l’IDE appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> et le document récemment ouvert de site.

    3. Enfin, l’IDE charge le document à l’aide de l’interface de persistance habituelles, telles que <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.

    4. Si l’IDE a déterminé précédemment que la hiérarchie ou un élément de la hiérarchie est disponible, l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> méthode sur le projet pour obtenir un contexte au niveau du projet <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> pointeur à retourner dans avec la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> appel de méthode.

4. Retourner un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> pointeur à l’IDE lorsque l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> sur votre projet si vous souhaitez que l’Éditeur du contexte Obtenir contexte à partir de votre projet.

     Cette étape permet les projet offre des services supplémentaires à l’éditeur.

     Si la vue de document ou d’un objet de vue de document a été correctement placé dans un frame de fenêtre, l’objet est initialisé avec ses données en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)
- [Guide pratique pour Ouvrez éditeurs spécifiques du projet](../extensibility/how-to-open-project-specific-editors.md)
- [Guide pratique pour Ouvrir des éditeurs pour les documents ouverts](../extensibility/how-to-open-editors-for-open-documents.md)
- [Afficher les fichiers à l’aide de la commande Ouvrir un fichier](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)