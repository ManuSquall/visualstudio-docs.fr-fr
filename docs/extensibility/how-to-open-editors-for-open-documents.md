---
title: "Comment : ouvrir des &#233;diteurs pour les Documents ouverts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), ouvrir des documents ouverts"
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment : ouvrir des &#233;diteurs pour les Documents ouverts
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Avant qu'un projet ouvre une fenêtre de document, d'abord le fichier doit déterminer si le fichier est déjà ouvert dans la fenêtre de document pour un autre éditeur.  Le fichier peut être ouvert dans un éditeur spécifique au projet, ou l'un des éditeurs standard enregistrés avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Ouvrir un éditeur spécifique au projet  
 Utilisez la procédure suivante pour ouvrir un éditeur spécifique aux projets pour un fichier déjà ouvert.  
  
#### Pour ouvrir un éditeur spécifique aux projets pour un fichier ouvert  
  
1.  Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.  
  
     Cet appel retourne des pointeurs vers la hiérarchie du document, à l'élément de hiérarchie, et au frame de fenêtre, le cas échéant.  
  
2.  Si le document est ouvert, le projet doit vérifier si un seul objet de données du document existe, ou si un objet de vue du document est également présent.  
  
    -   Si un objet de vue du document existe, et cette vue est pour une hiérarchie ou un élément différente de la hiérarchie, le projet utilise le pointeur au frame de fenêtre de la vue pour reblanchir la fenêtre existante.  
  
    -   Si un objet de vue du document existe, et cette vue est pour la même hiérarchie et élément de hiérarchie, le projet peut ouvrir une deuxième vue s'il peut être attaché à l'objet de données sous\-jacent de document.  Sinon, le projet doit utiliser le pointeur au frame de fenêtre de la vue pour reblanchir la fenêtre existante.  
  
    -   Si seul l'objet de données du document existe, le projet doit déterminer s'il peut utiliser l'objet de données du document pour sa vue.  Si l'objet de données du document est compatible, exécutez les étapes décrites dans [Ouvrir un éditeur spécifique au projet](../extensibility/how-to-open-project-specific-editors.md).  
  
     Si l'objet de données du document n'est pas compatible, une erreur doit être affichée à l'utilisateur qui indique que le fichier est en cours de utilisation.  Cette erreur ne doit être affichées dans les cas transitional, par exemple lorsqu'un fichier est compilé en même temps l'utilisateur essaie d'ouvrir le fichier à l'aide d'un éditeur autre que l'éditeur de texte principal de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Le principal éditeur de texte peut partager l'objet de données du document avec le compilateur.  
  
3.  Si le document n'est pas ouvert car il n'existe aucun objet de données du document ou objet de vue du document, exécutez les étapes dans [Ouvrir un éditeur spécifique au projet](../extensibility/how-to-open-project-specific-editors.md).  
  
## ouvrir un éditeur standard  
 Utilisez la procédure suivante pour ouvrir un éditeur standard pour un fichier déjà ouvert.  
  
#### pour ouvrir un éditeur standard pour un fichier ouvert  
  
1.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     cette méthode vérifie d'abord que le document n'est pas déjà ouvert par <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>appelant.  Si le document est déjà ouvert, la fenêtre de l'éditeur est reblanchie.  
  
2.  Si le document n'est pas ouvert, puis remplissez les étapes de [Comment : ouvrir les éditeurs Standard](../extensibility/how-to-open-standard-editors.md).  
  
## Voir aussi  
 [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Comment : ouvrir les éditeurs spécifiques au projet](../extensibility/how-to-open-project-specific-editors.md)   
 [Comment : ouvrir les éditeurs Standard](../extensibility/how-to-open-standard-editors.md)