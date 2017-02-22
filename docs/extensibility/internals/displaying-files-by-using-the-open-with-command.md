---
title: "Afficher les fichiers &#224; l&#39;aide de l&#39;ouvrir avec la commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "types de projets, prise en charge de la commande Ouvrir avec"
  - "Commande Ouvrir avec"
  - "persistance, prise en charge de la commande Ouvrir avec"
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Afficher les fichiers &#224; l&#39;aide de l&#39;ouvrir avec la commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un projet peut demander à l'IDE pour afficher la boîte de dialogue d' **Ouvrir avec** .  Cette demande invite l'utilisateur à ouvrir un fichier qui a une sélection des éditeurs standard.  les étapes suivantes décrivent ce processus.  
  
1.  Le projet appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, en spécifiant une valeur d'OSE\_UseOpenWithDialog pour le paramètre d' `OSEOpenDocEditor` .  
  
2.  En fonction de l'extension de nom de fichier du document, l'IDE détermine les éditeurs répertoriés dans le Registre peuvent ouvrir le document spécifié et affiche ces informations dans la boîte de dialogue d' **Ouvrir avec** .  
  
    > [!NOTE]
    >  Les projets qui ont un éditeur intrinsèque qui doit être inclus dans la boîte de dialogue d' **Ouvrir avec** doivent signaler une fabrique d'éditeur pour chacun de ces éditeur.  Les éditeurs intrinsèques fonctionnent uniquement avec le type de projet particulier, qui est appliqué dans l'implémentation de la méthode de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .  L'IDE a une fabrique intégrée d'éditeur pour le principal éditeur de texte et l'éditeur binaire.  L'IDE crée également une instance d'une fabrique d'éditeur au nom de chaque association enregistrée de fichiers Windows.  un exemple d'un tel fichier est Microsoft Word.  
  
3.  Dès que l'utilisateur sélectionne un élément dans la boîte de dialogue d' **Ouvrir avec** , l'IDE puis ouvre le document par méthode d'appel d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  Pour plus d'informations, consultez [Comment : ouvrir les éditeurs Standard](../../extensibility/how-to-open-standard-editors.md).  
  
## Voir aussi  
 [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Afficher les fichiers à l'aide de la commande Ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Comment : ouvrir les éditeurs Standard](../../extensibility/how-to-open-standard-editors.md)