---
title: 'Le Concepteur de flux de travail - Comment : créer une Application Console de Workflow'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6461a644bdedd3d391059cd8a3a17f887e77c6b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970898"
---
# <a name="how-to-create-a-workflow-console-application"></a>Procédure : créer une application console de workflow

Windows Workflow Foundation (WF) vous permet de créer des workflows pour l’exécution des processus système ou humains. Le Concepteur de flux de travail Windows fournit l’aire de conception pour la création de ces flux de travail. Le Concepteur de Workflow peut être utilisé pour créer des flux de travail à partir de Visual Studio, ou il peut être intégré dans d’autres applications pour réhéberger le concepteur.

Cette rubrique décrit comment utiliser le Concepteur de flux de travail dans Visual Studio 2010 pour créer un flux de travail dans une application console.

## <a name="to-create-a-workflow-console-application"></a>Pour créer une application console de workflow

1.  Démarrez Visual Studio 2010.

2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s'affiche.

3.  Dans le **modèles installés** volet, sélectionnez **Workflow** à partir de le le **Visual C#** ou **Visual Basic** regroupements, en fonction de votre langue de préférence.

4.  Dans le volet central, sélectionnez **Application Console de Workflow**.

5.  Dans le **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

6.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur la zone **Parcourir** pour naviguer jusqu'à lui.

7.  Dans le **Solution** , entrez le nom de la nouvelle solution. Cliquez sur **OK** pour créer l’application.

    > [!NOTE]
    > Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans Visual Studio 2010, cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions**, puis sélectionnez **ajouter**, puis  **Nouveau projet** pour ouvrir le **nouveau projet** boîte de dialogue. Procédez comme décrit ci-dessus dans cette procédure.

8.  Le modèle de projet crée une définition de workflow en XAML et la définition d'application console se trouve dans le code source. Le Concepteur de flux de travail s’ouvre et affiche la zone de dessin du flux de travail que vous avez créé.

9. Pour composer un workflow, faites glisser les activités ou autres éléments de flux de travail à partir de la **boîte à outils** vers l’aire de conception de votre flux de travail.

## <a name="see-also"></a>Voir aussi

- [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)