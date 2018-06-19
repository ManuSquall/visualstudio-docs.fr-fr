---
title: 'Le Concepteur de flux de travail - Comment : créer un projet de Workflow vide (héritée)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- projects, empty workflow
- empty workflow projects
- workflows, empty workflow projects
ms.assetid: f81b9cf2-9adb-47a2-936b-cb1851614e19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2aa51df35a1187c8d327a401d77c12e4532f4eb8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979436"
---
# <a name="how-to-create-an-empty-workflow-project-legacy"></a>Procédure : créer un projet de workflow vide (héritée)

Suivez ces étapes pour créer un projet de Workflow vide l’aide du Concepteur de flux de travail Windows hérité fournis par Visual Studio 2010. Utilisez le Concepteur de flux de travail hérité lorsque vous avez besoin cibler le .NET Framework version 3.5 ou du WinFX.

## <a name="to-create-an-empty-workflow-project"></a>Pour créer un projet de workflow vide

1.  Démarrez Visual Studio.

2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s'affiche.

3.  Sélectionnez le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre pour accéder au concepteur hérité.

    > [!NOTE]
    > L’option par défaut dans Visual Studio 2010 est **.NET Framework 4**. Cette option est utilisée pour créer des applications de Windows Workflow Foundation (WF) qui ciblent le .NET Framework 4, et il n’utilise pas le concepteur hérité.

4.  Dans le **Types de projets** volet, sélectionnez Visual c# ou Visual Basic (sous **autres langages**), puis sélectionnez **Workflow**.

5.  Dans le **modèles** volet, sélectionnez **projet de Workflow vide**.

6.  Dans le **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

7.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur la zone **Parcourir** pour naviguer jusqu'à lui.

     Si vous souhaitez un répertoire de solution créé pour le projet, sélectionnez le **créer le répertoire pour la solution** case à cocher et entrez un nom dans la **nom de la Solution** boîte.

8.  Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)