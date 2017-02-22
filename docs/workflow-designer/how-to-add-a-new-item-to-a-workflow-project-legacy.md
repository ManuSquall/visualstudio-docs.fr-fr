---
title: "Proc&#233;dure&#160;: ajouter un nouvel &#233;l&#233;ment &#224; un projet de workflow (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "activités, ajouter à des projets de workflow"
  - "workflows séquentiels, ajouter à des projets de workflow"
  - "workflows d'ordinateur d'état, ajouter à des projets de workflow"
  - "workflows, ajouter de nouveaux éléments"
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Proc&#233;dure&#160;: ajouter un nouvel &#233;l&#233;ment &#224; un projet de workflow (h&#233;rit&#233;e)
Après avoir créé un projet de workflow à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité fourni par [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], vous pouvez ajouter à votre projet des éléments [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] et d'autres éléments [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui vous sont familiers.  
  
 Le tableau suivant répertorie les éléments [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] que vous pouvez ajouter à un projet de workflow.  
  
|Élément|Description|  
|-------------|-----------------|  
|Activité|Activité contenant une définition d'activité dans le fichier de code du concepteur et le code utilisateur dans un fichier de code séparé.|  
|Activité \(avec séparation de code\)|Définition d'activité exprimée sous forme de balisage du workflow et de code utilisateur contenu dans un fichier de code séparé.|  
|Workflow séquentiel \(code\)|Workflow séquentiel avec définition de workflow contenue dans un fichier de code concepteur et un code utilisateur contenu dans un fichier de code séparé.|  
|Workflow séquentiel \(avec séparation de code\)|Workflow séquentiel avec définition de workflow exprimée sous forme de balisage du workflow et code utilisateur contenu dans un fichier de code séparé.|  
|Workflow de l'ordinateur d'état \(code\)|Workflow d'ordinateur d'état avec définition de workflow contenue dans un fichier de code concepteur et un code utilisateur contenu dans un fichier de code séparé.|  
|Workflow de l'ordinateur d'état \(avec séparation de code\)|Workflow de l'ordinateur d'état avec définition de workflow exprimée sous forme de balisage du workflow et code utilisateur contenu dans un fichier de code séparé.|  
  
### Pour ajouter un nouvel élément à un projet de workflow  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément**  s'ouvre.  
  
2.  Sélectionnez un élément.  
  
     Le tableau précédent répertorie les sélections Windows Workflow Foundation disponibles.  
  
3.  Cliquez sur **Ajouter** pour ajouter un élément au projet de workflow.  
  
## Voir aussi  
 [Création de projets de workflows hérités](../workflow-designer/creating-legacy-workflow-projects.md)