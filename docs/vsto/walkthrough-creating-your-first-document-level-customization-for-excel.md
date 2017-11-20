---
title: "Procédure pas à pas : Création de votre première personnalisation au niveau du Document pour Excel | Documents Microsoft"
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
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
ms.assetid: 785d3b86-5ed5-4e0d-b5ee-896b6b1330ac
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 046f5376891c62278b3756078f82b9e5db3b28d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-your-first-document-level-customization-for-excel"></a>Procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel
  Cette procédure pas à pas d'introduction vous indique comment créer une personnalisation au niveau du document pour Microsoft Office Excel. Les fonctionnalités que vous créez dans ce genre de solution sont disponibles uniquement quand un classeur spécifique est ouvert. Vous ne pouvez pas utiliser une personnalisation au niveau du document pour apporter des changements à l'échelle de l'application, par exemple afficher un nouvel onglet de ruban quand un classeur est ouvert.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet de classeur Excel.  
  
-   Ajout de texte à une feuille de calcul hébergée dans le concepteur Visual Studio.  
  
-   Écriture de code qui utilise le modèle objet d'Excel pour ajouter du texte à la feuille de calcul personnalisée quand elle est ouverte.  
  
-   Génération et exécution du projet pour le tester.  
  
-   Nettoyage du projet achevé pour supprimer les fichiers de build et les paramètres de sécurité inutiles de votre ordinateur de développement.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
  
#### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Pour créer un projet de classeur Excel dans Visual Studio  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.  
  
4.  Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .  
  
5.  Dans la liste des modèles de projet, choisissez un projet de complément Excel VSTO.  
  
6.  Dans le **nom** , tapez **FirstWorkbookCustomization**.  
  
7.  Cliquez sur **OK**.  
  
     L' **Assistant Projet Visual Studio Tools pour Office** s'ouvre.  
  
8.  Sélectionnez **créer un nouveau document**, puis cliquez sur **OK**.  
  
    -   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]crée le **FirstWorkbookCustomization** le projet, puis ajoute les fichiers suivants au projet.  
  
    -   *FirstWorkbookCustomization*.xlsx - représente le classeur Excel dans le projet. Contient l'ensemble des feuilles de calcul et des graphiques.  
  
    -   Feuil1 (fichier .vb pour Visual Basic ou fichier .cs pour Visual C#) - Feuille de calcul qui fournit l'aire de conception et le code de la première feuille de calcul dans le classeur. Pour plus d'informations, consultez [Worksheet Host Item](../vsto/worksheet-host-item.md).  
  
    -   Feuil2 (fichier .vb pour Visual Basic ou fichier .cs pour Visual C#) - Feuille de calcul qui fournit l'aire de conception et le code de la deuxième feuille de calcul dans le classeur.  
  
    -   Feuil3 (fichier .vb pour Visual Basic ou fichier .cs pour Visual C#) - Feuille de calcul qui fournit l'aire de conception et le code de la troisième feuille de calcul dans le classeur.  
  
    -   ThisWorkbook (fichier .vb pour Visual Basic ou fichier .cs pour Visual C#) - Contient l'aire de conception et le code pour les personnalisations au niveau du classeur. Pour plus d'informations, consultez [Workbook Host Item](../vsto/workbook-host-item.md).  
  
     Le fichier de code Feuil1 est ouvert automatiquement dans le concepteur.  
  
## <a name="closing-and-reopening-worksheets-in-the-designer"></a>Fermeture et réouverture des feuilles de calcul dans le concepteur  
 Si vous fermez délibérément ou accidentellement un classeur ou une feuille de calcul dans le concepteur pendant que vous développez votre projet, vous pouvez le rouvrir.  
  
#### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Pour fermer et rouvrir une feuille de calcul dans le concepteur  
  
1.  Fermez le classeur en cliquant sur le **fermer** bouton (X) de la fenêtre du concepteur.  
  
2.  Dans **l’Explorateur de solutions**, avec le bouton droit le **Feuil1** fichier de code, puis cliquez sur **Concepteur de vue**.  
  
     \- ou -  
  
     Dans **l’Explorateur de solutions**, double-cliquez sur le **Feuil1** fichier de code.  
  
## <a name="adding-text-to-a-worksheet-in-the-designer"></a>Ajout de texte à une feuille de calcul dans le concepteur  
 Vous pouvez concevoir l'interface utilisateur de votre personnalisation en modifiant la feuille de calcul ouverte dans le concepteur. Par exemple, vous pouvez ajouter du texte aux cellules, appliquer des formules ou ajouter des contrôles Excel. Pour plus d’informations sur l’utilisation du concepteur, consultez [les projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Pour ajouter une feuille de calcul à votre document à l'aide du concepteur  
  
1.  Dans la feuille de calcul ouverte dans le concepteur, sélectionnez la cellule **A1**, puis tapez le texte suivant.  
  
     **Ce texte a été ajouté à l’aide du concepteur.**  
  
> [!WARNING]  
>  Si vous ajoutez cette ligne de texte à la cellule **A2**, il sera remplacé par un autre code dans cet exemple.  
  
## <a name="adding-text-to-a-worksheet-programmatically"></a>Ajout de texte à une feuille de calcul par programmation  
 L'étape suivante consiste à ajouter du code au fichier de code Feuil1. Le nouveau code utilise le modèle objet d'Excel pour ajouter une deuxième ligne de texte au classeur. Par défaut, le fichier de code Feuil1 contient le code généré suivant :  
  
-   Une définition partielle de la classe `Sheet1`, qui représente le modèle de programmation de la feuille de calcul et permet d'accéder au modèle objet d'Excel. Pour plus d’informations, [élément hôte de feuille de calcul](../vsto/worksheet-host-item.md) et [présentation du modèle objet de Word](../vsto/word-object-model-overview.md). Le reste de la classe `Sheet1` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `Sheet1_Startup` et `Sheet1_Shutdown`. Ces gestionnaires d'événements sont appelés quand Excel charge et décharge votre personnalisation. Utilisez ces gestionnaires d'événements pour initialiser votre personnalisation quand elle est chargée, ainsi que pour nettoyer les ressources utilisées par votre personnalisation quand elle est déchargée. Pour plus d'informations, consultez [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Pour ajouter une deuxième ligne de texte à la feuille de calcul en utilisant du code  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **Feuil1**, puis cliquez sur **afficher le Code**.  
  
     Le fichier de code s'ouvre dans Visual Studio.  
  
2.  Remplacez le gestionnaire d'événements `Sheet1_Startup` par le code suivant. Quand Feuil1 est ouvert, ce code ajoute une deuxième ligne de texte à la feuille de calcul.  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]  
  
## <a name="testing-the-project"></a>Test du projet  
  
#### <a name="to-test-your-workbook"></a>Pour tester votre classeur  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet.  
  
     Quand vous générez le projet, le code est compilé dans un assembly qui est associé au classeur. Visual Studio place une copie du classeur et de l’assembly dans le dossier de sortie de la génération du projet. Par ailleurs, il configure les paramètres de sécurité sur l’ordinateur de développement pour permettre l’exécution de la personnalisation. Pour plus d’informations, consultez [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
2.  Dans le classeur, vérifiez que vous voyez le texte suivant.  
  
     **Ce texte a été ajouté à l’aide du concepteur.**  
  
     **Ce texte a été ajouté via le code.**  
  
3.  Fermez le classeur.  
  
## <a name="cleaning-up-the-project"></a>Nettoyage du projet  
 Une fois que vous avez fini de développer un projet, vous devez supprimer les fichiers du dossier de sortie de génération et les paramètres de sécurité créés par le processus de génération.  
  
#### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Pour nettoyer le projet terminé sur votre ordinateur de développement  
  
1.  Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une fois que vous avez créé une personnalisation de base au niveau du document pour Excel, vous pouvez en apprendre plus sur la manière de développer des personnalisations dans les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les personnalisations au niveau du document : [programmation de personnalisations au niveau du Document](../vsto/programming-document-level-customizations.md).  
  
-   Tâches de programmation sont aux personnalisations au niveau du document pour Excel : [Solutions Excel](../vsto/excel-solutions.md).  
  
-   Utilisation du modèle objet d’Excel : [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
-   Personnalisation de l’interface utilisateur d’Excel, par exemple, en ajoutant un onglet personnalisé au ruban ou en créant votre propre volet actions : [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
-   À l’aide des objets Excel étendus fournis par les outils de développement Office dans Visual Studio pour effectuer des tâches qui ne sont pas possibles en utilisant le modèle objet Excel (par exemple, héberger des contrôles managés sur des documents et lier des contrôles Excel aux données à l’aide de Windows Forms modèle de liaison de données) : [automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md).  
  
-   Génération et débogage des personnalisations au niveau du document pour Excel : [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement de personnalisations au niveau du document pour Excel : [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du développement de Solutions Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Solutions Excel](../vsto/excel-solutions.md)   
 [Programmation des personnalisations au niveau du Document](../vsto/programming-document-level-customizations.md)   
 [Vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Génération de Solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  