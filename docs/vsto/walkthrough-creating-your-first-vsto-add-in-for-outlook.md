---
title: "Procédure pas à pas : Création de votre complément VSTO pour Outlook | Documents Microsoft"
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
- Outlook [Office development in Visual Studio], creating your first project
ms.assetid: 2c5c5d75-27ee-471f-9328-58f0cf05b2b7
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 514e6e0f52867b586135050d555508caec8cb6e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-outlook"></a>Procédure pas à pas : création de votre premier complément VSTO pour Outlook
  Cette procédure pas à pas montre comment créer un complément VSTO pour Microsoft Office Outlook. Les fonctionnalités que vous créez dans ce type de solution sont accessibles à l'application elle-même, quel que soit l'élément Outlook ouvert. Pour plus d’informations, consultez [présentation du développement de Solutions Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un projet de complément VSTO Outlook pour Outlook.  
  
-   Écriture du code qui utilise le modèle objet d'Outlook pour ajouter du texte à l'objet et au corps d'un nouveau message électronique.  
  
-   Génération et exécution du projet pour le tester  
  
-   Nettoyage du projet terminé, pour que le complément VSTO ne s’exécute plus automatiquement sur votre ordinateur de développement  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## <a name="creating-the-project"></a>Création du projet  
  
#### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Pour créer un projet Outlook dans Visual Studio  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.  
  
4.  Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .  
  
5.  Dans la liste des modèles de projet, sélectionnez un projet de complément VSTO Outlook.  
  
6.  Dans la zone **Nom** , tapez **FirstOutlookAddIn**.  
  
7.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet **FirstOutlookAddIn** et ouvre le fichier de code **ThisAddIn** dans l'éditeur.  
  
## <a name="writing-code-that-adds-text-to-each-new-mail-message"></a>Écriture du code qui ajoute du texte à chaque nouveau message électronique  
 L'étape suivante consiste à ajouter du code au fichier de code ThisAddIn. Le nouveau code utilise le modèle objet d'Outlook pour ajouter du texte à chaque nouveau message électronique. Par défaut, le fichier de code ThisAddIn contient le code généré suivant :  
  
-   Une définition partielle de la classe `ThisAddIn` . Cette classe fournit un point d'entrée pour votre code et offre un accès au modèle objet d'Outlook. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). Le reste de la classe `ThisAddIn` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `ThisAddIn_Startup` et `ThisAddIn_Shutdown` . Ces gestionnaires d’événements sont appelés quand Outlook charge et décharge votre complément VSTO. Utilisez ces gestionnaires d'événements pour initialiser votre complément VSTO quand il est chargé, ainsi que pour nettoyer les ressources utilisées par votre complément VSTO quand il est déchargé. Pour plus d'informations, consultez [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Pour ajouter du texte à l'objet et au corps de chaque nouveau message électronique  
  
1.  Dans le fichier de code ThisAddIn, déclarez un champ nommé `inspectors` dans la classe `ThisAddIn` . Le champ `inspectors` conserve une référence à la collection de fenêtres Inspecteur de l'instance Outlook actuelle. Cette référence empêche le garbage collector de libérer la mémoire qui contient le gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .  
  
     [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Remplacez la méthode `ThisAddIn_Startup` par le code suivant. Ce code attache un gestionnaire d'événements à l'événement <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .  
  
     [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
     [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]  
  
3.  Dans le fichier de code ThisAddIn, ajoutez le code suivant à la classe `ThisAddIn` . Ce code définit un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .  
  
     Lorsque l'utilisateur crée un message électronique, ce gestionnaire d'événements ajoute du texte à l'objet et au corps du message.  
  
     [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
     [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]  
  
 Pour modifier chaque nouveau message électronique, les exemples de code précédents utilisent les objets suivants :  
  
-   Le champ `Application` de la classe `ThisAddIn` . Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.Outlook.Application> qui représente l'instance actuelle d'Outlook.  
  
-   Le paramètre `Inspector` du gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> . Le paramètre `Inspector` est un objet <xref:Microsoft.Office.Interop.Outlook.Inspector> , qui représente la fenêtre Inspecteur du nouveau message électronique. Pour plus d'informations, consultez [Outlook Solutions](../vsto/outlook-solutions.md).  
  
## <a name="testing-the-project"></a>Test du projet  
 Lorsque vous générez et exécutez le projet, vérifiez que le texte s'affiche dans la ligne d'objet et le corps d'un nouveau message électronique.  
  
#### <a name="to-test-the-project"></a>Pour tester le projet  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet.  
  
     Quand vous générez le projet, le code est compilé dans un assembly qui est inclus dans le dossier de sortie de la génération du projet. Visual Studio crée également un jeu d’entrées de Registre qui permet à Outlook de détecter et de charger le complément VSTO, et il configure les paramètres de sécurité de l’ordinateur de développement pour permettre au complément VSTO de s’exécuter. Pour plus d'informations, consultez [Office Solution Build Process Overview](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).  
  
2.  Dans Outlook, créez un nouveau message électronique.  
  
3.  Vérifiez que le texte suivant est ajouté à la ligne d'objet et au corps du message.  
  
     **Ce texte a été ajouté via le code.**  
  
4.  Fermez Outlook.  
  
## <a name="cleaning-up-the-project"></a>Nettoyage du projet  
 Une fois que vous avez terminé de développer un projet, supprimez l'assembly du complément VSTO, les entrées de Registre et les paramètres de sécurité de votre ordinateur de développement. Sinon, le complément VSTO s’exécutera chaque fois que vous ouvrirez Outlook sur l’ordinateur de développement.  
  
#### <a name="to-clean-up-your-project"></a>Pour nettoyer votre projet  
  
1.  Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez créé un complément VSTO de base pour Outlook, vous pouvez perfectionner votre connaissance du développement des compléments VSTO en consultant les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer à l’aide des compléments VSTO pour Outlook. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Utilisation du modèle objet d'Outlook Pour plus d'informations, consultez [Outlook Solutions](../vsto/outlook-solutions.md).  
  
-   Personnalisation de l'interface utilisateur d'Outlook en ajoutant un onglet personnalisé au ruban ou en créant votre propre volet des tâches personnalisé. Pour plus d’informations, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
-   Génération et débogage des compléments VSTO pour Outlook. Pour plus d’informations, consultez [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement des compléments VSTO pour Outlook. Pour plus d’informations, consultez [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Solutions Outlook](../vsto/outlook-solutions.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Génération de Solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  