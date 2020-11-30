---
title: Affichage des fichiers à l’aide de la commande Ouvrir avec | Microsoft Docs
description: Découvrez comment un projet peut appeler la commande Ouvrir avec dans l’environnement de développement intégré (IDE) de Visual Studio pour afficher des fichiers.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f2cb6bd44148d470cac68addc09db9e9207e9d70
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329690"
---
# <a name="display-files-by-using-the-open-with-command"></a>Afficher les fichiers à l’aide de la commande Ouvrir avec
Un projet peut demander à l’IDE d’afficher la boîte de dialogue **Ouvrir avec** . Cette demande invite l’utilisateur à ouvrir un fichier qui a une sélection de éditeurs standard. Les étapes suivantes décrivent ce processus :

1. Le projet appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , en spécifiant une valeur `OSE_UseOpenWithDialog` pour le `OSEOpenDocEditor` paramètre.

2. En fonction de l’extension de nom de fichier du document, l’IDE détermine les éditeurs listés dans le Registre qui peuvent ouvrir le document spécifié et affiche ces informations dans la boîte de dialogue **Ouvrir avec** .

    > [!NOTE]
    > Les projets qui ont un éditeur intrinsèque qui doit être inclus dans la boîte de dialogue **Ouvrir avec** doivent inscrire une fabrique d’éditeur pour chacun de ces éditeurs. Les éditeurs intrinsèques fonctionnent uniquement avec un type particulier de projet, qui est appliqué dans l’implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode. L’IDE dispose d’une fabrique d’éditeur intégrée pour l’éditeur de texte principal et l’éditeur binaire. L’IDE crée également une instance d’une fabrique d’éditeur pour le compte de chaque association de fichiers Windows enregistrée. Microsoft Word est un exemple de ce type de fichier.

3. Dès que l’utilisateur sélectionne un élément dans la boîte de dialogue **Ouvrir avec** , l’IDE ouvre le document en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode. Pour plus d’informations, consultez [Comment : ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Voir aussi
- [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)
- [Afficher les fichiers à l’aide de la commande ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Procédure : ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)
