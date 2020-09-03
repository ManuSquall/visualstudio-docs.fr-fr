---
title: 'Comment : ajouter un nouvel élément à un projet de workflow (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 46f6e9daafc2688b9bea75cba9eddd8c8a53c9bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656671"
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

1. Dans le menu **projet** , cliquez sur **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

2. Sélectionnez un élément.

     Le tableau précédent répertorie les sélections Windows Workflow Foundation disponibles.

3. Cliquez sur **Ajouter** pour ajouter l’élément au projet de Workflow.

## <a name="see-also"></a>Voir aussi
 [Création de projets de workflows hérités](../workflow-designer/creating-legacy-workflow-projects.md)