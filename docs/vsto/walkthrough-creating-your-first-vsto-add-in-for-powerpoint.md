---
title: "Procédure pas à pas : Création de votre complément VSTO pour PowerPoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
ms.assetid: 52d1543a-c9cb-4ee1-aa5b-90759fce9d3a
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3d0f0a2162c4144c6a9fd67650d467b9828a3add
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-powerpoint"></a>Procédure pas à pas : création de votre premier complément VSTO pour PowerPoint
  Cette procédure pas à pas montre comment créer un complément VSTO pour Microsoft Office PowerPoint. Les fonctionnalités que vous créez dans ce type de solution sont accessibles à l’application, quelles que soient les présentations ouvertes. Pour plus d’informations, consultez [présentation du développement de Solutions Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   création d'un projet de complément PowerPoint VSTO pour PowerPoint ;  
  
-   écriture de code utilisant le modèle objet de PowerPoint pour ajouter une zone de texte à chaque nouvelle diapositive ;  
  
-   Génération et exécution du projet pour le tester  
  
-   nettoyage du projet pour que le complément VSTO ne s’exécute plus automatiquement sur votre ordinateur de développement.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## <a name="creating-the-project"></a>Création du projet  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.  
  
4.  Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .  
  
5.  Dans la liste des modèles de projet, sélectionnez un projet de complément PowerPoint VSTO.  
  
6.  Dans le **nom** , tapez **FirstPowerPointAddIn**.  
  
7.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]crée le **FirstPowerPointAddIn** projet et ouvre le **ThisAddIn** fichier de code dans l’éditeur.  
  
## <a name="writing-code-that-adds-text-to-each-new-slide"></a>Écriture du code qui ajoute du texte à chaque nouvelle diapositive  
 L'étape suivante consiste à ajouter du code au fichier de code ThisAddIn. Le nouveau code utilise le modèle objet de PowerPoint pour ajouter une zone de texte à chaque nouvelle diapositive. Par défaut, le fichier de code ThisAddIn contient le code généré suivant :  
  
-   Une définition partielle de la classe `ThisAddIn` . Cette classe fournit un point d'entrée pour votre code et offre un accès au modèle objet de PowerPoint. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). Le reste de la classe `ThisAddIn` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `ThisAddIn_Startup` et `ThisAddIn_Shutdown` . Ces gestionnaires d'événements sont appelés quand PowerPoint charge et décharge votre complément VSTO. Utilisez ces gestionnaires d'événements pour initialiser votre complément VSTO quand il est chargé, ainsi que pour nettoyer les ressources utilisées par votre complément VSTO quand il est déchargé. Pour plus d'informations, consultez [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-text-box-to-each-new-slide"></a>Pour ajouter une zone de texte à chaque nouvelle diapositive  
  
1.  Dans le fichier de code ThisAddIn, ajoutez le code suivant à la classe `ThisAddIn` . Ce code définit un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> de l'objet <xref:Microsoft.Office.Interop.PowerPoint.Application>.  
  
     Quand l'utilisateur ajoute une nouvelle diapositive à la présentation active, ce gestionnaire d'événements ajoute une zone de texte en haut de la nouvelle diapositive, puis ajoute du texte à la zone de texte.  
  
     [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]  
  
2.  En C#, ajoutez le code suivant au gestionnaire d'événements `ThisAddIn_Startup` . Ce code est indispensable pour connecter le gestionnaire d'événements `Application_PresentationNewSlide` à l'événement <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]  
  
 Pour modifier chaque nouvelle diapositive, les exemples de code précédents utilisent les objets suivants :  
  
-   Le champ `Application` de la classe `ThisAddIn` . Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.PowerPoint.Application> qui représente l'instance actuelle de PowerPoint.  
  
-   Le paramètre `Sld` du gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>. Le paramètre `Sld` est un objet <xref:Microsoft.Office.Interop.PowerPoint.Slide>, qui représente la nouvelle diapositive. Pour plus d’informations, consultez [Solutions PowerPoint](../vsto/powerpoint-solutions.md).  
  
## <a name="testing-the-project"></a>Test du projet  
 Quand vous générez et exécutez le projet, vérifiez que la zone de texte apparaît dans les nouvelles diapositives que vous ajoutez à une présentation.  
  
#### <a name="to-test-the-project"></a>Pour tester le projet  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet.  
  
     Quand vous générez le projet, le code est compilé dans un assembly qui est placé dans le dossier de sortie de la génération du projet. Visual Studio crée également un jeu d’entrées du Registre qui permet à PowerPoint de détecter et de charger le complément VSTO. Par ailleurs, il configure les paramètres de sécurité de l’ordinateur de développement pour permettre au complément VSTO de s’exécuter. Pour plus d’informations, consultez [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
2.  Dans PowerPoint, ajoutez une nouvelle diapositive à la présentation active.  
  
3.  Vérifiez que le texte suivant est ajouté à une nouvelle zone de texte en haut de la diapositive.  
  
     **Ce texte a été ajouté via le code.**  
  
4.  Fermez PowerPoint.  
  
## <a name="cleaning-up-the-project"></a>Nettoyage du projet  
 Une fois que vous avez fini de développer un projet, supprimez l'assembly de complément VSTO, les entrées du Registre et les paramètres de sécurité de votre ordinateur de développement. Sinon, le complément VSTO s’exécutera chaque fois que vous ouvrirez PowerPoint sur votre ordinateur.  
  
#### <a name="to-clean-up-your-project"></a>Pour nettoyer votre projet  
  
1.  Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une fois que vous avez créé un complément VSTO de base pour PowerPoint, vous pouvez perfectionner votre connaissance du développement des compléments VSTO en consultant les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les compléments VSTO pour PowerPoint. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Utilisation du modèle objet de PowerPoint. Pour plus d’informations, consultez [Solutions PowerPoint](../vsto/powerpoint-solutions.md).  
  
-   Personnalisation de l’interface utilisateur de PowerPoint en ajoutant un onglet personnalisé au ruban, ou en créant votre propre volet des tâches personnalisé. Pour plus d’informations, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
-   Génération et débogage des compléments VSTO pour PowerPoint. Pour plus d’informations, consultez [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement des compléments VSTO pour PowerPoint. Pour plus d’informations, consultez [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Solutions PowerPoint](../vsto/powerpoint-solutions.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Génération de Solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  