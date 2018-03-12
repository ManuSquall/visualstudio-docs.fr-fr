---
title: "Comment : ajouter un nouvel élément à un projet de Workflow (hérité) | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d2b0c644854f8f08ff7aeeb05f92fe3fd359f45e
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>Procédure : ajouter un nouvel élément à un projet de workflow (héritée)
Après avoir créé un projet de flux de travail utilisant le Concepteur de flux de travail Windows hérité fourni par [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], vous pouvez ajouter [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] éléments et autres familière [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] d’éléments à votre projet.

 Le tableau suivant répertorie les éléments [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] que vous pouvez ajouter à un projet de workflow.

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

3.  Cliquez sur **ajouter** pour ajouter un élément au projet de workflow.

## <a name="see-also"></a>Voir aussi

- [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)