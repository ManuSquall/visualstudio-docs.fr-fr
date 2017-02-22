---
title: "Projet fichiers divers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers, ajouter des fichiers existants à des solutions"
  - "Projet fichiers divers"
  - "Dossier éléments de solution"
  - "fichiers, ouverture avec le projet fichiers divers"
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Projet fichiers divers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsqu'un utilisateur ouvre des éléments de projet, l'IDE assigne au projet Fichiers divers tous les éléments qui ne sont pas membres d'un projet dans une solution.  
  
 Les projets jouent un rôle important pour déterminer quel éditeur est utilisé lorsqu'un utilisateur ouvre un élément de projet.  Un projet peut être conçu pour ouvrir certains fichiers à l'aide d'un éditeur spécifique au projet ou d'un éditeur standard.  
  
 Un éditeur spécifique au projet requiert généralement que l'utilisateur a une connaissance particulière ou les interfaces spéciales du projet.  Pour plus d'informations, consultez [Comment : ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Un éditeur standard peut ouvrir les fichiers d'une extension spécifique dans tout projet.  L'utilisateur peut personnaliser certains éditeurs standard, tels que l'éditeur de texte de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , car projets mais conserver leur caractère public.  Les éditeurs standard sont créés à l'aide de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
 Si aucun projet de la solution ne répond qu'il peut ouvrir un élément de projet, l'IDE fournit un projet spécial appelé le projet Fichiers divers qui ouvre un fichier.  
  
 Ce projet spécial fournit l'ouverture d'un fichier en dehors de le contexte d'un projet.  Pendant le traitement de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> , le projet Fichiers divers continue avec très une priorité basse.  Par conséquent, le projet Fichiers divers donne toujours à tout projet plus élevée qui peut ouvrir des fichiers.  
  
 Le projet Fichiers divers ne nécessite pas d'utilisateur à créer explicitement avec la boîte de dialogue de **Nouveau projet** .  en outre, le projet Fichiers divers ne gère pas définitivement une liste de membres du projet.  Il utilise une fonctionnalité en option pour stocker une liste des derniers fichiers utilisés pour chaque utilisateur.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Comment : ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md)   
 [Comment : ouvrir les éditeurs Standard](../../extensibility/how-to-open-standard-editors.md)   
 [Ajout de projet et modèles d'élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Ajout de projet et modèles d'élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)