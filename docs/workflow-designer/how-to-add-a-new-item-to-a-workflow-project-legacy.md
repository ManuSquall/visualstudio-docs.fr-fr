---
title: 'Le Concepteur de flux de travail - Comment : ajouter un nouvel élément à un projet de Workflow (héritée)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d6e9607f4924057568849fd7eabd4567130dc2f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974233"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>Procédure : ajouter un nouvel élément à un projet de workflow (héritée)

Après avoir créé un projet de flux de travail à l’aide du Concepteur de flux de travail Windows fournies par Visual Studio 2010 qui cible le .NET Framework version 3.5 ou du WinFX hérité, vous pouvez ajouter des éléments de Windows Workflow Foundation (WF) et autres Visual Studio familier éléments à votre projet.

Le tableau suivant répertorie les éléments Windows Workflow Foundation que vous pouvez ajouter à un projet de workflow.

|Élément|Description|
|----------|-----------------|
|Activité|Activité contenant une définition d'activité dans le fichier de code du concepteur et le code utilisateur dans un fichier de code séparé.|
|Activité (avec séparation de code)|Définition d'activité exprimée sous forme de balisage du workflow et de code utilisateur contenu dans un fichier de code séparé.|
|Workflow séquentiel (code)|Workflow séquentiel avec définition de workflow contenue dans un fichier de code concepteur et un code utilisateur contenu dans un fichier de code séparé.|
|Workflow séquentiel (avec séparation de code)|Workflow séquentiel avec définition de workflow exprimée sous forme de balisage du workflow et code utilisateur contenu dans un fichier de code séparé.|
|Workflow de l'ordinateur d'état (code)|Workflow d'ordinateur d'état avec définition de workflow contenue dans un fichier de code concepteur et un code utilisateur contenu dans un fichier de code séparé.|
|Workflow de l'ordinateur d'état (avec séparation de code)|Workflow de l'ordinateur d'état avec définition de workflow exprimée sous forme de balisage du workflow et code utilisateur contenu dans un fichier de code séparé.|

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Pour ajouter un nouvel élément à un projet de workflow

1.  Sur le **projet** menu, cliquez sur **ajouter un nouvel élément**.

     Le **ajouter un nouvel élément** boîte de dialogue s’ouvre.

2.  Sélectionnez un élément.

     Le tableau précédent répertorie les sélections Windows Workflow Foundation disponibles.

3.  Cliquez sur **ajouter** pour ajouter un élément au projet de workflow.

## <a name="see-also"></a>Voir aussi

- [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)