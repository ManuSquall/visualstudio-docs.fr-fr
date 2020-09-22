---
title: Affichage des fichiers à l’aide de la commande Ouvrir avec | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de43b6c4f441f8c6bde2d6c248274aed3937a7ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839437"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Affichage de fichiers à l’aide de la commande Ouvrir avec
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un projet peut demander à l’IDE d’afficher la boîte de dialogue **Ouvrir avec** . Cette demande invite l’utilisateur à ouvrir un fichier qui a une sélection de éditeurs standard. Les étapes de ce processus sont décrites ci-dessous.  
  
1. Le projet appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , en spécifiant une valeur de OSE_UseOpenWithDialog pour le `OSEOpenDocEditor` paramètre.  
  
2. En fonction de l’extension de nom de fichier du document, l’IDE détermine les éditeurs listés dans le Registre qui peuvent ouvrir le document spécifié et affiche ces informations dans la boîte de dialogue **Ouvrir avec** .  
  
    > [!NOTE]
    > Les projets qui ont un éditeur intrinsèque qui doit être inclus dans la boîte de dialogue **Ouvrir avec** doivent inscrire une fabrique d’éditeur pour chacun de ces éditeurs. Les éditeurs intrinsèques fonctionnent uniquement avec un type particulier de projet, qui est appliqué dans l’implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode. L’IDE dispose d’une fabrique d’éditeur intégrée pour l’éditeur de texte principal et l’éditeur binaire. L’IDE crée également une instance d’une fabrique d’éditeur pour le compte de chaque association de fichiers Windows enregistrée. Microsoft Word est un exemple de ce type de fichier.  
  
3. Dès que l’utilisateur sélectionne un élément dans la boîte de dialogue **Ouvrir avec** , l’IDE ouvre le document en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode. Pour plus d’informations, consultez [Comment : ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Affichage de fichiers à l’aide de la commande ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)
