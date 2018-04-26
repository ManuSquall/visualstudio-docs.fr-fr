---
title: 'Le Concepteur de flux de travail - Comment : créer des Applications de Console de Workflow séquentiel (héritée)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb4e048fdf8eb8fee541f84656a29427b5a07a1d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Procédure : créer des applications console de workflow séquentiel (héritée)

Suivez ces étapes pour créer un projet d’Application Console de Workflow séquentiel à l’aide de l’héritage Concepteur de flux de travail Windows fourni par Visual Studio 2010. Utilisez le Concepteur de flux de travail hérité lorsque vous avez besoin cibler le .NET Framework version 3.5 ou du WinFX.

## <a name="to-create-a-sequential-workflow-console-application"></a>Pour créer une application console de workflow séquentiel

1.  Démarrez Visual Studio.

2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s'affiche.

3.  Sélectionnez le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre pour accéder au concepteur hérité.

    > [!NOTE]
    > L’option par défaut dans Visual Studio 2010 est **.NET Framework 4**. Cette option est utilisée pour créer des applications de Windows Workflow Foundation (WF) qui ciblent le .NET Framework 4, et il n’utilise pas le concepteur hérité.

4.  Dans le **Types de projets** volet, sélectionnez projets Visual c# ou Visual Basic (sous **autres langages**), puis sélectionnez **Workflow**.

5.  Dans le **modèles** volet, sélectionnez **Application Console de Workflow séquentiel**.

6.  Dans le **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

7.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur la zone **Parcourir** pour naviguer jusqu'à lui.

     Le Concepteur Windows Forms s'ouvre et affiche le Form1 du projet que vous avez créé.

8.  Cliquez sur **OK**.

     Le Concepteur de flux de travail s'ouvre et affiche l'aire de conception de workflow du workflow séquentiel créé.

9. Faites glisser une activité de la **boîte à outils** vers l’aire de conception dans le **déposer l’activité** zone désignée.

## <a name="see-also"></a>Voir aussi

- [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)
- [Développement de flux de travail](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)