---
title: 'Comment : ajouter un nouvel élément à un projet de flux de travail (hérité) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 1a0ccdc10a76f8c8bc594130bcba5210190fb34a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495726"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>Procédure : ajouter un nouvel élément à un projet de workflow (héritée)
Après avoir créé un projet de workflow à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité fourni par [!INCLUDE[vs2010](../includes/vs2010-md.md)] qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], vous pouvez ajouter à votre projet des éléments [!INCLUDE[wf](../includes/wf-md.md)] et d'autres éléments [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui vous sont familiers.  
  
 Le tableau suivant répertorie les éléments [!INCLUDE[wf2](../includes/wf2-md.md)] que vous pouvez ajouter à un projet de workflow.  
  
|Élément|Description|  
|----------|-----------------|  
|Activité|Activité contenant une définition d'activité dans le fichier de code du concepteur et le code utilisateur dans un fichier de code séparé.|  
|Activité (avec séparation de code)|Définition d'activité exprimée sous forme de balisage du workflow et de code utilisateur contenu dans un fichier de code séparé.|  
|Workflow séquentiel (code)|Workflow séquentiel avec définition de workflow contenue dans un fichier de code concepteur et un code utilisateur contenu dans un fichier de code séparé.|  
|Workflow séquentiel (avec séparation de code)|Workflow séquentiel avec définition de workflow exprimée sous forme de balisage du workflow et code utilisateur contenu dans un fichier de code séparé.|  
|Workflow de l'ordinateur d'état (code)|Workflow d'ordinateur d'état avec définition de workflow contenue dans un fichier de code concepteur et un code utilisateur contenu dans un fichier de code séparé.|  
|Workflow de l'ordinateur d'état (avec séparation de code)|Workflow de l'ordinateur d'état avec définition de workflow exprimée sous forme de balisage du workflow et code utilisateur contenu dans un fichier de code séparé.|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>Pour ajouter un nouvel élément à un projet de workflow  
  
1.  Sur le **projet** menu, cliquez sur **ajouter un nouvel élément**.  
  
     Le **ajouter un nouvel élément** boîte de dialogue s’ouvre.  
  
2.  Sélectionnez un élément.  
  
     Le tableau précédent répertorie les sélections Windows Workflow Foundation disponibles.  
  
3.  Cliquez sur **ajouter** pour ajouter l’élément au projet de workflow.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)