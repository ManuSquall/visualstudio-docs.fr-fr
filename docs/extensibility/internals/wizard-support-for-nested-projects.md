---
title: "Prise en charge de l&#39;Assistant de projets imbriqu&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ajouter l'Assistant élément"
  - "prise en charge de l'Assistant, les projets imbriqués"
  - "Assistant Nouveau projet"
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Prise en charge de l&#39;Assistant de projets imbriqu&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'IDE exécute deux Assistant que le projet parent pour les projets imbriqués peut implémenter : l'Assistant de **Nouveau projet** et l'Assistant d' **Ajouter un élément** .  
  
 Si un utilisateur démarre l'Assistant de **Nouveau projet** en sélectionnant **Ajouter un projet** et en cliquant sur **Nouveau projet** dans le menu Fichier ou sélectionner **Ajouter** et en cliquant avec le bouton droit sur l'explorateur de **Nouveau projet** en solution, l'IDE exécute la commande d' **AddProject** et l'implémentation de projet parent de la commande d' **AddProject** retourne un fichier projet de modèle, ou un fichier de l'Assistant \(.vsz\) contenant un jeu de paramètres de contexte.  
  
 De même, une implémentation de projet parent des assistants d' **AddItem** retourne un fichier .vsz qui a un autre ensemble de paramètres de contexte.  
  
 Pour plus d'informations sur les assistants, consultez [Assistant \(. Fichier vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md), [Paramètres de contexte](../../extensibility/internals/context-parameters.md) et l' [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Projets d'imbrication](../../extensibility/internals/nesting-projects.md)