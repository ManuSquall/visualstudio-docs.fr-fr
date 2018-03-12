---
title: "Procédure pas à pas : Création de votre complément VSTO pour Excel | Documents Microsoft"
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
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: de2b241cd44adebecd91ee097ebf8f8875915937
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-excel"></a>Procédure pas à pas : création de votre premier complément VSTO pour Excel
  Cette procédure pas à pas d'introduction vous indique comment créer un complément de niveau application pour Microsoft Office Excel. Les fonctionnalités que vous créez dans ce type de solution sont accessibles à l'application, quels que soient les classeurs ouverts.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet de complément VSTO Excel pour Excel  
  
-   Écriture de code qui utilise le modèle objet d'Excel pour ajouter du texte à un classeur quand il est enregistré.  
  
-   Génération et exécution du projet pour le tester  
  
-   Nettoyage du projet terminé, pour que le complément VSTO ne s’exécute plus automatiquement sur votre ordinateur de développement  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Pour créer un projet de complément VSTO Excel dans Visual Studio  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.  
  
4.  Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .  
  
5.  Dans la liste des modèles de projet, sélectionnez **Complément Excel 2010** ou **Complément Excel 2013**.  
  
6.  Dans la zone **Nom** , tapez **FirstExcelAddIn**.  
  
7.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet **FirstExcelAddIn** et ouvre le fichier de code ThisAddIn dans l'éditeur.  
  
## <a name="writing-code-to-add-text-to-the-saved-workbook"></a>Écriture de code pour ajouter du texte au classeur enregistré  
 L'étape suivante consiste à ajouter du code au fichier de code ThisAddIn. Le nouveau code utilise le modèle objet d'Excel pour insérer du texte réutilisable dans la première ligne de la feuille de calcul active. La feuille de calcul active est celle qui est ouverte quand l'utilisateur enregistre le classeur. Par défaut, le fichier de code ThisAddIn contient le code généré suivant :  
  
-   Une définition partielle de la classe `ThisAddIn` . Cette classe fournit un point d'entrée pour votre code et offre un accès au modèle objet d'Excel. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). Le reste de la classe `ThisAddIn` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `ThisAddIn_Startup` et `ThisAddIn_Shutdown` . Ces gestionnaires d'événements sont appelés quand Excel charge et décharge votre complément VSTO. Utilisez ces gestionnaires d'événements pour initialiser votre complément VSTO quand il est chargé et pour nettoyer les ressources utilisées par votre complément quand il est déchargé. Pour plus d'informations, consultez [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Pour ajouter une ligne de texte au classeur enregistré  
  
1.  Dans le fichier de code ThisAddIn, ajoutez le code suivant à la classe `ThisAddIn` . Le nouveau code définit un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> qui est déclenché quand un classeur est enregistré.  
  
     Quand l'utilisateur enregistre un classeur, le gestionnaire d'événements ajoute le nouveau texte au début de la feuille de calcul active.  
  
     [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Si vous utilisez C#, ajoutez le code requis suivant au gestionnaire d'événements `ThisAddIn_Startup` . Ce code permet de connecter le gestionnaire d'événements `Application_WorkbookBeforeSave` à l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> .  
  
     [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]  
  
 Pour modifier le classeur quand il est enregistré, les exemples de code précédents utilisent les objets suivants :  
  
-   Le champ `Application` de la classe `ThisAddIn` . Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.Excel.Application> qui représente l'instance actuelle d'Excel.  
  
-   Le paramètre `Wb` du gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> . Le paramètre `Wb` est un objet <xref:Microsoft.Office.Interop.Excel.Workbook> qui représente le classeur enregistré. Pour plus d'informations, consultez [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
## <a name="testing-the-project"></a>Test du projet  
  
#### <a name="to-test-the-project"></a>Pour tester le projet  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet.  
  
     Quand vous générez le projet, le code est compilé dans un assembly qui est inclus dans le dossier de sortie de la génération du projet. Visual Studio crée également un jeu d'entrées de Registre qui permet à Excel de détecter et de charger le complément VSTO, et il configure les paramètres de sécurité de l'ordinateur de développement pour permettre au complément VSTO de s'exécuter. Pour plus d’informations, consultez [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
2.  Dans Excel, enregistrez le classeur.  
  
3.  Vérifiez que le texte suivant est ajouté au classeur.  
  
     **Ce texte a été ajouté via le code.**  
  
4.  Fermez Excel.  
  
## <a name="cleaning-up-the-project"></a>Nettoyage du projet  
 Une fois que vous avez terminé de développer un projet, supprimez l'assembly du complément VSTO, les entrées de Registre et les paramètres de sécurité de votre ordinateur de développement. Sinon, le complément VSTO s'exécute chaque fois que vous ouvrez Excel sur votre ordinateur de développement.  
  
#### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Pour nettoyer le projet terminé sur votre ordinateur de développement  
  
1.  Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez créé un complément VSTO de base pour Excel, vous pouvez perfectionner votre connaissance du développement des compléments VSTO en consultant les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les compléments VSTO : [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Tâches de programmation propres aux compléments VSTO Excel : [Excel Solutions](../vsto/excel-solutions.md).  
  
-   Utilisation du modèle objet d’Excel : [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
-   Personnalisation de l’interface utilisateur (IU) de Microsoft Excel, par exemple, en ajoutant un onglet personnalisé au ruban ou en créant votre propre volet de tâches personnalisé : [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
-   Génération et débogage des Compléments VSTO pour Excel : [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement de compléments VSTO pour Excel : [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du développement de Solutions Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Solutions Excel](../vsto/excel-solutions.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Génération de Solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  