---
title: 'Comment : Ouvrir les rédacteurs spécifiques au projet (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710841"
---
# <a name="how-to-open-project-specific-editors"></a>Comment : Ouvrir les éditeurs spécifiques au projet
Si un fichier d’objets ouvert par un projet est intrinsèquement lié à l’éditeur particulier pour ce projet, le projet doit ouvrir le fichier à l’aide d’un éditeur spécifique au projet. Le fichier ne peut pas être délégué au mécanisme de l’IDE pour la sélection d’un éditeur. Par exemple, au lieu d’utiliser un éditeur de bitmap standard, vous pouvez utiliser cette option d’éditeur spécifique au projet pour spécifier un éditeur de bitmap spécifique qui reconnaît les informations dans le fichier qui est unique à votre projet.

 L’IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> appelle la méthode lorsqu’il détermine qu’un fichier doit être ouvert par un projet spécifique. Pour plus d’informations, voir [les fichiers Display en utilisant la commande Open File](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Utilisez les lignes directrices suivantes pour mettre en œuvre la `OpenItem` méthode permettant à votre projet d’ouvrir un fichier en utilisant un éditeur spécifique au projet.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Mettre en œuvre la méthode OpenItem avec un éditeur spécifique au projet

1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> la`RDT_EditLock`méthode ( ) pour déterminer si le fichier (objet de données documentaires) est déjà ouvert.

    > [!NOTE]
    > Pour plus d’informations sur les données documentaires et les documents, consultez [les données du Document et la vue des documents dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Si le fichier est déjà ouvert, refait <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> surface le fichier en appelant la `grfIDO` méthode et en spécifiant une valeur de IDO_ActivateIfOpen pour le paramètre.

     Si le fichier est ouvert et que le document appartient à un projet autre que le projet d’appel, un avertissement sera affiché à l’utilisateur que l’éditeur en cours d’ouverture provient d’un autre projet. La fenêtre du fichier est alors refaite surface.

3. Si votre tampon texte (objet de données de document) est déjà ouvert et que vous souhaitez y joindre une autre vue, vous êtes responsable de brancher cette vue. L’approche recommandée pour instantanéiser une vue (objet de vue documentaire) du projet est la suivante :

    1. Faites `QueryService` appel <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> au service pour <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> obtenir un pointeur à l’interface.

    2. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> la méthode pour créer une instance de la classe de vue de document.

4. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> la méthode, en spécifiant votre objet de vue de document.

     Cette méthode permet de visualiser l’objet dans une fenêtre de document.

5. Effectuez les appels <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> appropriés <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> aux méthodes ou aux méthodes.

     À ce stade, le point de vue devrait être entièrement parasécé et prêt à être ouvert.

6. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> la méthode pour montrer et ouvrir la vue.

## <a name="see-also"></a>Voir aussi
- [Ouvrir et enregistrer les éléments du projet](../extensibility/internals/opening-and-saving-project-items.md)
- [Comment : Ouvrir les éditeurs standard](../extensibility/how-to-open-standard-editors.md)
- [Comment : Ouvrir les éditeurs pour les documents ouverts](../extensibility/how-to-open-editors-for-open-documents.md)
