---
title: 'Le Concepteur de flux de travail - Comment : créer une bibliothèque d’activités de Workflow (héritée)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 432766e60ee1384db0f8cd5bad1f369e80ddd20a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Procédure : créer une bibliothèque d'activités de workflow (héritée)

Suivez ces étapes pour créer un projet de bibliothèque d’activités de flux de travail à l’aide de l’héritage Concepteur de flux de travail Windows fourni par Visual Studio 2010. Utilisez le Concepteur de flux de travail hérité lorsque vous avez besoin cibler le .NET Framework version 3.5 ou du WinFX.

## <a name="to-create-a-workflow-activity-library-project"></a>Pour créer un projet de bibliothèque d'activité de workflow

1.  Démarrez Visual Studio.

2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s'affiche.

3.  Sélectionnez le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre pour accéder au concepteur hérité.

    > [!NOTE]
    > L’option par défaut dans Visual Studio 2010 est **.NET Framework 4**. Cette option est utilisée pour créer des applications de Windows Workflow Foundation (WF) qui ciblent le .NET Framework 4, et il n’utilise pas le concepteur hérité.

4.  Dans le **Types de projets** volet, sélectionnez Visual c# ou Visual Basic (sous **autres langages**), puis sélectionnez **Workflow**.

5.  Dans le **modèles** volet, sélectionnez **bibliothèque d’activités de flux de travail**.

6.  Dans le **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

7.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur la zone **Parcourir** pour naviguer jusqu'à lui.

     Si vous souhaitez un répertoire de solution créé pour le projet, sélectionnez le **créer le répertoire pour la solution** case à cocher et entrez un nom dans la **nom de la Solution** boîte.

8.  Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)
- [Utilisation du concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)
- [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)
- [Développement des activités de flux de travail](http://msdn.microsoft.com/en-us/19876dfc-dfa5-4d52-b1f5-1d087474cc52)
- [Activités Windows Workflow Foundation](http://msdn.microsoft.com/en-us/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)