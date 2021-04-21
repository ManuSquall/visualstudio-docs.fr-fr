---
title: 'Procédure pas à pas : créer votre premier complément VSTO pour Project'
description: Créez un complément de niveau application pour Microsoft Project. Cette fonctionnalité est disponible pour l’application elle-même, quels que soient les projets ouverts.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 48d7baf9605947818ffd79eb7312c0dbefe581ac
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824261"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Procédure pas à pas : créer votre premier complément VSTO pour Project
  Cette procédure pas à pas vous montre comment créer un complément VSTO pour Microsoft Office projet. Les fonctionnalités que vous créez dans ce type de solution sont accessibles à l’application proprement dite, quels que soient les projets ouverts. Pour plus d’informations, consultez [vue d’ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un projet de complément VSTO Project

- Écriture de code qui utilise le modèle objet de Project pour ajouter une tâche à un nouveau projet

- Génération et exécution du projet pour le tester

- Nettoyage du projet terminé, pour que le complément VSTO ne s’exécute plus automatiquement sur votre ordinateur de développement

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] ou [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].

## <a name="create-the-project"></a>Créer le projet

### <a name="to-create-a-new-project-in-visual-studio"></a>Pour créer un projet dans Visual Studio

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3. Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.

4. Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .

5. Dans la liste des modèles de projet, sélectionnez **Complément Project 2010** ou **Complément Project 2013**.

6. Dans la zone **Nom** , tapez **FirstProjectAddIn**.

7. Cliquez sur **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet **FirstProjectAddIn** et ouvre le fichier de code **ThisAddIn** dans l’éditeur.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Écrire du code qui ajoute une nouvelle tâche à un projet
 L'étape suivante consiste à ajouter du code au fichier de code ThisAddIn. Le nouveau code utilise le modèle objet de Project pour ajouter une nouvelle tâche à un projet. Par défaut, le fichier de code ThisAddIn contient le code généré suivant :

- Une définition partielle de la classe `ThisAddIn` . Cette classe fournit un point d’entrée pour votre code et donne accès au modèle objet de Project. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md). Le reste de la `ThisAddIn` classe est défini dans un fichier de code masqué que vous ne devez pas modifier.

- Les gestionnaires d'événements `ThisAddIn_Startup` et `ThisAddIn_Shutdown` . Ces gestionnaires d’événements sont appelés quand Project charge et décharge votre complément VSTO. Utilisez ces gestionnaires d'événements pour initialiser votre complément VSTO quand il est chargé, ainsi que pour nettoyer les ressources utilisées par votre complément VSTO quand il est déchargé. Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-task-to-a-new-project"></a>Pour ajouter une tâche à un nouveau projet

1. Dans le fichier de code ThisAddIn, ajoutez le code suivant à la classe `ThisAddIn` . Ce code définit un gestionnaire d’événements pour l’événement `NewProject` de la classe `Microsoft.Office.Interop.MSProject.Application`.

    Quand l’utilisateur crée un projet, ce gestionnaire d’événements ajoute une tâche au projet.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs" id="Snippet1":::

   Pour modifier le projet, cet exemple de code utilise les objets suivants :

- Le champ `Application` de la classe `ThisAddIn` . Le champ `Application` retourne un objet `Microsoft.Office.Interop.MSProject.Application` qui représente l’instance active de Project.

- `pj`Paramètre du gestionnaire d’événements pour l’événement NewProject. Le paramètre `pj` est un objet `Microsoft.Office.Interop.MSProject.Project` qui représente le projet. Pour plus d’informations, consultez [solutions de projet](../vsto/project-solutions.md).

1. En C#, ajoutez le code suivant au gestionnaire d'événements `ThisAddIn_Startup` . Ce code connecte le `Application_Newproject` Gestionnaire d’événements à l’événement NewProject.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs" id="Snippet2":::

## <a name="test-the-project"></a>Tester le projet
 Quand vous générez et exécutez le projet, vérifiez que la nouvelle tâche apparaît dans le nouveau projet obtenu.

### <a name="to-test-the-project"></a>Pour tester le projet

1. Appuyez sur **F5** pour générer et exécuter votre projet. Microsoft Project démarre et ouvre automatiquement un nouveau projet vide.

     Quand vous générez le projet, le code est compilé dans un assembly qui est inclus dans le dossier de sortie de la génération du projet. Visual Studio crée aussi un jeu d’entrées de Registre qui permet à Project de détecter et de charger le complément VSTO, puis configure les paramètres de sécurité sur l’ordinateur de développement pour permettre l’exécution du complément VSTO. Pour plus d’informations, consultez [vue d’ensemble du processus de génération de solutions Office](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).

2. Vérifiez qu’une nouvelle tâche est bien ajoutée au projet vierge.

3. Vérifiez que le texte suivant s’affiche dans le champ **Nom de la tâche** de la tâche.

     **Ce texte a été ajouté via le code.**

4. Fermez Microsoft Project.

## <a name="clean-up-the-project"></a>Nettoyer le projet
 Une fois que vous avez terminé de développer un projet, supprimez l'assembly du complément VSTO, les entrées de Registre et les paramètres de sécurité de votre ordinateur de développement. Sinon, le complément VSTO s’exécute chaque fois que vous ouvrez Microsoft Project sur votre ordinateur.

### <a name="to-clean-up-your-project"></a>Pour nettoyer votre projet

1. Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.

## <a name="next-steps"></a>Étapes suivantes
 Maintenant que vous avez créé un complément VSTO de base pour Project, vous pouvez en savoir plus sur le développement des compléments VSTO en consultant les rubriques suivantes :

- Tâches de programmation générales que vous pouvez effectuer dans les compléments VSTO pour Project : [programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md).

- Utilisation du modèle objet de Project : [solutions de projet](../vsto/project-solutions.md).

- Génération et débogage des compléments VSTO pour Project : [créer des solutions Office](../vsto/building-office-solutions.md).

- Déploiement de compléments VSTO pour Project : [déployer une solution Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Voir aussi
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Solutions de projet](../vsto/project-solutions.md)
- [Créer des solutions Office](../vsto/building-office-solutions.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
- [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)
