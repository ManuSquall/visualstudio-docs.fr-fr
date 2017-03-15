---
title: "Priorit&#233; du projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets (Visual Studio SDK), l'ouverture d'éléments"
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Priorit&#233; du projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un élément de projet est généralement un membre d'un seul projet dans la solution.  Par conséquent, l'IDE peut facilement déterminer le projet est utilisé pour ouvrir l'élément.  Toutefois, si un élément est membre de plusieurs projet, l'IDE utilise un schéma de priorité pour déterminer le meilleur projet pour l'ouvrir.  
  
 La liste suivante présente le modèle de priorité de projet :  
  
-   L'IDE appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> pour chaque projet dans la solution pour déterminer si le document est membre de ce projet.  
  
-   Si le document est membre du projet, ce dernier répond avec une priorité que le projet assigne selon sa gestion de ce document.  Par exemple, un projet de langue répond à une haute priorité pour ses fichiers sources du langage mais répond avec une priorité plus faible pour un type de fichier non reconnu qui n'est pas utilisé dans le cadre de son processus de génération.  
  
-   Les projets qui fournissent le personnalisé, les éditeurs spécifiques au projet ou les concepteurs pour un document également acceptent une priorité supérieure.  
  
-   L'énumération d' <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> fournit des valeurs de priorité de document.  
  
-   Le projet qui spécifie la plus élevée est fourni le contexte pour ouvrir le document.  Si deux projets retournent des valeurs égales élevée, le projet actif est préféré.  Si aucun projet de la solution ne répond qu'il peut ouvrir le document, l'IDE ajoute le document dans le projet Fichiers divers.  Pour plus d'informations, consultez [Projet fichiers divers](../../extensibility/internals/miscellaneous-files-project.md).  
  
## Voir aussi  
 [Projet fichiers divers](../../extensibility/internals/miscellaneous-files-project.md)   
 [Comment : ouvrir des éditeurs pour les Documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Ajout de projet et modèles d'élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)