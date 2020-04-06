---
title: 'Comment : Ouvrez les rédacteurs standard Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710788"
---
# <a name="how-to-open-standard-editors"></a>Comment : Ouvrir les éditeurs standard
Lorsque vous ouvrez un éditeur standard, vous laissez l’IDE déterminer un éditeur standard pour un type de fichier désigné, au lieu de spécifier un éditeur spécifique au projet pour le fichier.

 Terminez la procédure <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> suivante pour mettre en œuvre la méthode. Cela ouvrira un fichier de projet dans un éditeur standard.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Mettre en œuvre la méthode OpenItem avec un éditeur standard

1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> `RDT_EditLock`( ) pour déterminer si le fichier d’objets de données de document est déjà ouvert.

2. Si le fichier est déjà ouvert, refait <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> surface au fichier `IDO_ActivateIfOpen` en `grfIDO` appelant la méthode, en spécifiant une valeur du paramètre.

     Si le fichier est ouvert et que le document appartient à un projet différent de celui du projet d’appel, votre projet reçoit un avertissement indiquant que l’éditeur en cours d’ouverture provient d’un autre projet. La fenêtre du fichier est alors refaite surface.

3. Si le document n’est pas ouvert ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> non`OSE_ChooseBestStdEditor`dans la table de document en cours d’exécution, appelez la méthode ( ) pour ouvrir un éditeur standard pour le fichier.

     Lorsque vous appelez la méthode, l’IDE effectue les tâches suivantes :

    1. L’IDE scanne les rédacteurs/guidEditorType/Extensions sous-clé dans le registre pour déterminer quel éditeur peut ouvrir le fichier et a la plus haute priorité pour ce faire.

    2. Une fois que l’IDE a déterminé quel <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>éditeur peut ouvrir le fichier, l’IDE appelle . La mise en œuvre de cette méthode par l’éditeur renvoie les informations qui sont nécessaires pour que l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> et sitee le document nouvellement ouvert.

    3. Enfin, l’IDE charge le document en utilisant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>l’interface de persistance habituelle, comme .

    4. Si l’IDE a déjà déterminé que l’élément de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> hiérarchie ou de hiérarchie est <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> disponible, l’IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> appelle la méthode du projet pour obtenir un pointeur de contexte au niveau du projet pour revenir avec l’appel de méthode.

4. Retournez <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> un pointeur à l’IDE lorsque l’IDE fait appel <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> à votre projet si vous souhaitez laisser l’éditeur obtenir le contexte de votre projet.

     L’exécution de cette étape permet au projet d’offrir des services supplémentaires à l’éditeur.

     Si l’objet de vue de document ou de vue de document a été <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>localisé avec succès dans un cadre de fenêtre, l’objet est initialisé avec ses données en appelant .

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Ouvrez et enregistrez les éléments du projet](../extensibility/internals/opening-and-saving-project-items.md)
- [Comment : Ouvrir les éditeurs spécifiques au projet](../extensibility/how-to-open-project-specific-editors.md)
- [Comment : Ouvrir les éditeurs pour les documents ouverts](../extensibility/how-to-open-editors-for-open-documents.md)
- [Afficher les fichiers en utilisant la commande Open File](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
