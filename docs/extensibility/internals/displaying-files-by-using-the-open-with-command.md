---
title: "Afficher les fichiers à l’aide de l’ouvrir avec la commande | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed8a19ce0cfb6a7936d61ff7a5855498d2010359
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Afficher les fichiers à l’aide de l’ouvrir avec la commande
Un projet peut demander à l’IDE pour afficher le **ouvrir avec** boîte de dialogue. Cette demande invite l’utilisateur à ouvrir un fichier qui possède une sélection d’éditeurs standards. Les étapes suivantes décrivent ce processus.  
  
1.  Les appels de projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, la valeur de OSE_UseOpenWithDialog pour la `OSEOpenDocEditor` paramètre.  
  
2.  En fonction de l’extension de nom de fichier du document, l’IDE détermine les éditeurs répertoriés dans le peut Registre ouvrir le document spécifié et affiche ces informations dans le **ouvrir avec** boîte de dialogue.  
  
    > [!NOTE]
    >  Les projets qui ont un éditeur intrinsèque qui doit être inclus dans le **ouvrir avec** boîte de dialogue doit inscrire une fabrique d’éditeur pour chaque éditeur de ce type. Éditeurs intrinsèques fonctionnent uniquement avec un type particulier de projet, qui est appliquée dans l’implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (méthode). L’IDE a une fabrique d’éditeur intégré pour l’éditeur de texte de base et l’éditeur binaire. L’interface IDE crée également une instance d’une fabrique d’éditeur pour le compte de chaque association de fichiers Windows inscrite. Un exemple d’un tel fichier est Microsoft Word.  
  
3.  Dès que l’utilisateur sélectionne un élément à partir de la **ouvrir avec** boîte de dialogue, puis l’IDE ouvre le document en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> (méthode). Pour plus d’informations, consultez [Comment : ouvrir les éditeurs Standard](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Afficher les fichiers à l’aide de la commande Ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)