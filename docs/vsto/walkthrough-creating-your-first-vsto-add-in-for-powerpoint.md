---
title: 'Procédure pas à pas : Créer votre premier complément pour PowerPoint'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cea6e61a1afd734ca0ae52a704a2d881371f5817
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882586"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>Procédure pas à pas : Créer votre premier complément pour PowerPoint
  Cette procédure pas à pas vous montre comment créer un complément, VSTO pour Microsoft Office PowerPoint. Les fonctionnalités que vous créez dans ce type de solution sont accessibles à l’application, quelles que soient les présentations ouvertes. Pour plus d’informations, consultez [présentation du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
- création d'un projet de complément PowerPoint VSTO pour PowerPoint ;  
  
- écriture de code utilisant le modèle objet de PowerPoint pour ajouter une zone de texte à chaque nouvelle diapositive ;  
  
- Génération et exécution du projet pour le tester  
  
- nettoyage du projet pour que le complément VSTO ne s’exécute plus automatiquement sur votre ordinateur de développement.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## <a name="create-the-project"></a>Créer le projet  
  
### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.  
  
4.  Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .  
  
5.  Dans la liste des modèles de projet, sélectionnez un projet de complément PowerPoint VSTO.  
  
6.  Dans le **nom** , tapez **FirstPowerPointAddIn**.  
  
7.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le **FirstPowerPointAddIn** projet et ouvre le **ThisAddIn** fichier de code dans l’éditeur.  
  
## <a name="write-code-that-adds-text-to-each-new-slide"></a>Écrire du code qui ajoute du texte à chaque nouvelle diapositive  
 L'étape suivante consiste à ajouter du code au fichier de code ThisAddIn. Le nouveau code utilise le modèle objet de PowerPoint pour ajouter une zone de texte à chaque nouvelle diapositive. Par défaut, le fichier de code ThisAddIn contient le code généré suivant :  
  
-   Une définition partielle de la classe `ThisAddIn` . Cette classe fournit un point d'entrée pour votre code et offre un accès au modèle objet de PowerPoint. Pour plus d’informations, consultez [programme VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Le reste de la classe `ThisAddIn` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `ThisAddIn_Startup` et `ThisAddIn_Shutdown` . Ces gestionnaires d'événements sont appelés quand PowerPoint charge et décharge votre complément VSTO. Utilisez ces gestionnaires d'événements pour initialiser votre complément VSTO quand il est chargé, ainsi que pour nettoyer les ressources utilisées par votre complément VSTO quand il est déchargé. Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-text-box-to-each-new-slide"></a>Pour ajouter une zone de texte à chaque nouvelle diapositive  
  
1. Dans le fichier de code ThisAddIn, ajoutez le code suivant à la classe `ThisAddIn` . Ce code définit un gestionnaire d’événements pour le [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) événements de la <xref:Microsoft.Office.Interop.PowerPoint.Application> objet.  
  
    Quand l'utilisateur ajoute une nouvelle diapositive à la présentation active, ce gestionnaire d'événements ajoute une zone de texte en haut de la nouvelle diapositive, puis ajoute du texte à la zone de texte.  
  
    [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]  
  
2. En C#, ajoutez le code suivant au gestionnaire d'événements `ThisAddIn_Startup` . Ce code est requis pour connecter le `Application_PresentationNewSlide` Gestionnaire d’événements avec le [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) événement.  
  
    [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]  
  
   Pour modifier chaque nouvelle diapositive, les exemples de code précédents utilisent les objets suivants :  
  
-   Le champ `Application` de la classe `ThisAddIn` . Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.PowerPoint.Application> qui représente l'instance actuelle de PowerPoint.  
  
-   Le `Sld` paramètre du Gestionnaire d’événements pour le [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) événement. Le paramètre `Sld` est un objet <xref:Microsoft.Office.Interop.PowerPoint.Slide>, qui représente la nouvelle diapositive. Pour plus d’informations, consultez [solutions PowerPoint](../vsto/powerpoint-solutions.md).  
  
## <a name="test-the-project"></a>Le projet de test  
 Quand vous générez et exécutez le projet, vérifiez que la zone de texte apparaît dans les nouvelles diapositives que vous ajoutez à une présentation.  
  
### <a name="to-test-the-project"></a>Pour tester le projet  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet.  
  
     Quand vous générez le projet, le code est compilé dans un assembly qui est placé dans le dossier de sortie de la génération du projet. Visual Studio crée également un jeu d’entrées du Registre qui permet à PowerPoint de détecter et de charger le complément VSTO. Par ailleurs, il configure les paramètres de sécurité de l’ordinateur de développement pour permettre au complément VSTO de s’exécuter. Pour plus d’informations, consultez [solutions Office Build](../vsto/building-office-solutions.md).  
  
2.  Dans PowerPoint, ajoutez une nouvelle diapositive à la présentation active.  
  
3.  Vérifiez que le texte suivant est ajouté à une nouvelle zone de texte en haut de la diapositive.  
  
     **Ce texte a été ajouté via le code.**  
  
4.  Fermez PowerPoint.  
  
## <a name="clean-up-the-project"></a>Nettoyer le projet  
 Une fois que vous avez terminé de développer un projet, supprimez l'assembly du complément VSTO, les entrées de Registre et les paramètres de sécurité de votre ordinateur de développement. Sinon, le complément VSTO s’exécutera chaque fois que vous ouvrirez PowerPoint sur votre ordinateur.  
  
### <a name="to-clean-up-your-project"></a>Pour nettoyer votre projet  
  
1.  Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une fois que vous avez créé un complément VSTO de base pour PowerPoint, vous pouvez perfectionner votre connaissance du développement des compléments VSTO en consultant les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les compléments VSTO pour PowerPoint. Pour plus d’informations, consultez [programme VSTO Add-ins](../vsto/programming-vsto-add-ins.md).  
  
-   Utilisation du modèle objet de PowerPoint. Pour plus d’informations, consultez [solutions PowerPoint](../vsto/powerpoint-solutions.md).  
  
-   Personnalisation de l’interface utilisateur de PowerPoint en ajoutant un onglet personnalisé au ruban, ou en créant votre propre volet des tâches personnalisé. Pour plus d’informations, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
-   Génération et débogage des compléments VSTO pour PowerPoint. Pour plus d’informations, consultez [solutions Office Build](../vsto/building-office-solutions.md).  
  
-   Déploiement des compléments VSTO pour PowerPoint. Pour plus d’informations, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Programmer des Compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Solutions PowerPoint](../vsto/powerpoint-solutions.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Générer des solutions Office](../vsto/building-office-solutions.md)   
 [Déployer une solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  