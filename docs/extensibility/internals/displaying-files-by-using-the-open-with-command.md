---
title: Affichage des fichiers en utilisant l’Open avec commande . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708580"
---
# <a name="display-files-by-using-the-open-with-command"></a>Afficher les fichiers en utilisant l’Open With command
Un projet peut demander à l’IDE d’afficher la boîte de dialogue **Open With.** Cette demande invite l’utilisateur à ouvrir un fichier qui a une sélection d’éditeurs standard. Les étapes suivantes décrivent ce processus :

1. Le projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>appelle , spécifiant une valeur de `OSE_UseOpenWithDialog` pour le `OSEOpenDocEditor` paramètre.

2. Sur la base de l’extension du nom de fichier du document, l’IDE détermine quels éditeurs énumérés dans le registre peuvent ouvrir le document spécifié et affiche ces informations dans la boîte de dialogue **Open With.**

    > [!NOTE]
    > Les projets qui ont un éditeur intrinsèque qui doit être inclus dans la boîte de dialogue **Open With** doivent enregistrer une usine d’éditeur pour chaque éditeur. Les éditeurs intrinsèques ne fonctionnent qu’avec un type particulier <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> de projet, qui est appliqué dans la mise en œuvre de la méthode. L’IDE dispose d’une usine d’éditeurs intégrée pour l’éditeur de texte de base et l’éditeur binaire. L’IDE crée également une instance d’une usine d’éditeurs pour le compte de chaque association de fichiers Windows enregistrée. Un exemple d’un tel fichier est Microsoft Word.

3. Dès que l’utilisateur sélectionne un élément de la boîte de dialogue Open <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> **With,** l’IDE ouvre ensuite le document en appelant la méthode. Pour plus d’informations, voir [Comment : Ouvrir les éditeurs standard](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Voir aussi
- [Ouvrez et enregistrez les éléments du projet](../../extensibility/internals/opening-and-saving-project-items.md)
- [Afficher les fichiers en utilisant la commande Open File](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Comment : Ouvrir les éditeurs standard](../../extensibility/how-to-open-standard-editors.md)
