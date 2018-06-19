---
title: 'Le Concepteur de flux de travail - Comment : créer une bibliothèque ActivityDesigner'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d05ddb48e88627f4b7ab4112c164b5129ddba910
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974589"
---
# <a name="how-to-create-an-activity-designer-library"></a>Procédure : créer une bibliothèque ActivityDesigner
Les concepteurs d'activités personnalisées vous permettent de créer une interface utilisateur pour une activité standard ou personnalisée. Vous contrôlez la complexité de l'interface utilisateur et avez la possibilité de créer plusieurs concepteurs d'activités pour une activité. Ce scénario vous permet de créer des concepteurs adaptés pour plusieurs audiences.

## <a name="to-create-an-activity-designer-library"></a>Pour créer une bibliothèque ActivityDesigner

1.  Démarrez Visual Studio 2010.

2.  Sur le **fichier** menu, pointez sur **nouveau**, puis sélectionnez **projet** pour ouvrir le **nouveau projet** boîte de dialogue.

3.  Dans le **Types de projets** volet, sélectionnez **Workflow** à partir de le le **Visual C#** ou **Visual Basic** regroupements en fonction de votre choix langage.

4.  Dans le **modèles** volet, sélectionnez **Bibliothèque ActivityDesigner**.

5.  Dans le **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

6.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur la zone **Parcourir** pour naviguer jusqu'à lui.

7.  Dans le **Solution** zone, tapez un nom descriptif pour votre solution, puis cliquez sur **OK**.

    > [!NOTE]
    > Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans Visual Studio 2010, cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions**, puis sélectionnez **ajouter**, puis **Nouveau projet** pour ouvrir le **nouveau projet** boîte de dialogue. Procédez comme décrit ci-dessus dans cette procédure.

8.  Le modèle de projet crée une définition de concepteur d'activités en XAML et le fichier d'implémentation code-behind dans le code source. Le Concepteur de flux de travail Windows s’ouvre et affiche la zone de dessin pour votre concepteur d’activités.

9. Windows Presentation Foundation (WPF) de faire glisser des contrôles de la **boîte à outils** vers l’aire de conception pour les utiliser dans votre concepteur d’activités personnalisées.  Pour obtenir un exemple montrant comment implémenter un concepteur d’activités personnalisées, consultez [Comment : créer un concepteur d’activités personnalisé](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

    > [!WARNING]
    > Concepteurs d’activités personnalisées peuvent être utilisés pour les activités personnalisées ainsi 4activities de .NET Framework par défaut.

## <a name="see-also"></a>Voir aussi

- [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)