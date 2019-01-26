---
title: 'Procédure pas à pas : Créer votre première personnalisation au niveau du document pour Excel'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eaf5fe98e5c5a9c54245307f50e71345d0e2d477
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871245"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Procédure pas à pas : Créer votre première personnalisation au niveau du document pour Excel
  Cette procédure pas à pas d'introduction vous indique comment créer une personnalisation au niveau du document pour Microsoft Office Excel. Les fonctionnalités que vous créez dans ce genre de solution sont disponibles uniquement quand un classeur spécifique est ouvert. Vous ne pouvez pas utiliser une personnalisation au niveau du document pour apporter des changements à l'échelle de l'application, par exemple afficher un nouvel onglet de ruban quand un classeur est ouvert.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
- Création d'un projet de classeur Excel.  
  
- Ajout de texte à une feuille de calcul hébergée dans le concepteur Visual Studio.  
  
- Écriture de code qui utilise le modèle objet d'Excel pour ajouter du texte à la feuille de calcul personnalisée quand elle est ouverte.  
  
- Génération et exécution du projet pour le tester  
  
- Nettoyage du projet achevé pour supprimer les fichiers de build et les paramètres de sécurité inutiles de votre ordinateur de développement.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Créer le projet  
  
### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Pour créer un projet de classeur Excel dans Visual Studio  
  
1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3. Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.  
  
4. Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .  
  
5. Dans la liste des modèles de projet, choisissez un projet de complément Excel VSTO.  
  
6. Dans le **nom** , tapez **FirstWorkbookCustomization**.  
  
7. Cliquez sur **OK**.  
  
    L' **Assistant Projet Visual Studio Tools pour Office** s'ouvre.  
  
8. Sélectionnez **créer un nouveau document**, puis cliquez sur **OK**.  
  
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le **FirstWorkbookCustomization** de projet et ajoute les fichiers suivants au projet.  
  
   - *FirstWorkbookCustomization*.xlsx - représente le classeur Excel dans le projet. Contient l'ensemble des feuilles de calcul et des graphiques.  
  
   - Sheet1 (*.vb* pour Visual Basic ou *.cs* fichier pour Visual c#)-feuille de calcul qui fournit l’aire de conception et le code pour la première feuille de calcul dans le classeur. Pour plus d’informations, consultez [élément hôte de feuille de calcul](../vsto/worksheet-host-item.md).  
  
   - Sheet2 (*.vb* pour Visual Basic ou *.cs* fichier pour Visual c#)-feuille de calcul qui fournit l’aire de conception et le code pour la deuxième feuille de calcul dans le classeur.  
  
   - Sheet3 (*.vb* pour Visual Basic ou *.cs* fichier pour Visual c#)-feuille de calcul qui fournit l’aire de conception et le code pour la troisième feuille de calcul dans le classeur.  
  
   - ThisWorkbook (*.vb* pour Visual Basic ou *.cs* fichier pour Visual c#)-contient l’aire de conception et le code pour les personnalisations au niveau du classeur. Pour plus d’informations, consultez [élément hôte de classeur](../vsto/workbook-host-item.md).  
  
     Le fichier de code Feuil1 est ouvert automatiquement dans le concepteur.  
  
## <a name="close-and-reopen-worksheets-in-the-designer"></a>Fermez et rouvrez le Concepteur de feuilles de calcul  
 Si vous fermez délibérément ou accidentellement un classeur ou une feuille de calcul dans le concepteur pendant que vous développez votre projet, vous pouvez le rouvrir.  
  
### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Pour fermer et rouvrir une feuille de calcul dans le concepteur  
  
1.  Fermez le classeur en cliquant sur le **fermer** bouton (X) de la fenêtre du concepteur.  
  
2.  Dans **l’Explorateur de solutions**, avec le bouton droit le **Sheet1** fichier de code, puis cliquez sur **Concepteur de vues**.  
  
     \- ou -  
  
     Dans **l’Explorateur de solutions**, double-cliquez sur le **Sheet1** fichier de code.  
  
## <a name="add-text-to-a-worksheet-in-the-designer"></a>Ajouter du texte à une feuille de calcul dans le Concepteur  
 Vous pouvez concevoir l'interface utilisateur de votre personnalisation en modifiant la feuille de calcul ouverte dans le concepteur. Par exemple, vous pouvez ajouter du texte aux cellules, appliquer des formules ou ajouter des contrôles Excel. Pour plus d’informations sur l’utilisation du concepteur, consultez [les projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Pour ajouter une feuille de calcul à votre document à l'aide du concepteur  
  
1.  Dans la feuille de calcul qui est ouvert dans le concepteur, sélectionnez la cellule **A1**, puis tapez le texte suivant.  
  
     **Ce texte a été ajouté à l’aide du concepteur.**  
  
> [!WARNING]  
>  Si vous ajoutez cette ligne de texte à la cellule **A2**, elle sera remplacée par un autre code dans cet exemple.  
  
## <a name="add-text-to-a-worksheet-programmatically"></a>Ajouter du texte à une feuille de calcul par programmation  
 L'étape suivante consiste à ajouter du code au fichier de code Feuil1. Le nouveau code utilise le modèle objet d'Excel pour ajouter une deuxième ligne de texte au classeur. Par défaut, le fichier de code Feuil1 contient le code généré suivant :  
  
-   Une définition partielle de la classe `Sheet1`, qui représente le modèle de programmation de la feuille de calcul et permet d'accéder au modèle objet d'Excel. Pour plus d’informations, [élément hôte de feuille de calcul](../vsto/worksheet-host-item.md) et [vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md). Le reste de la classe `Sheet1` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `Sheet1_Startup` et `Sheet1_Shutdown` . Ces gestionnaires d'événements sont appelés quand Excel charge et décharge votre personnalisation. Utilisez ces gestionnaires d'événements pour initialiser votre personnalisation quand elle est chargée, ainsi que pour nettoyer les ressources utilisées par votre personnalisation quand elle est déchargée. Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Pour ajouter une deuxième ligne de texte à la feuille de calcul en utilisant du code  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **Sheet1**, puis cliquez sur **afficher le Code**.  
  
     Le fichier de code s'ouvre dans Visual Studio.  
  
2.  Remplacez le gestionnaire d'événements `Sheet1_Startup` par le code suivant. Quand Feuil1 est ouvert, ce code ajoute une deuxième ligne de texte à la feuille de calcul.  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]  
  
## <a name="test-the-project"></a>Le projet de test  
  
### <a name="to-test-your-workbook"></a>Pour tester votre classeur  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet.  
  
     Quand vous générez le projet, le code est compilé dans un assembly qui est associé au classeur. Visual Studio place une copie du classeur et de l’assembly dans le dossier de sortie de la génération du projet. Par ailleurs, il configure les paramètres de sécurité sur l’ordinateur de développement pour permettre l’exécution de la personnalisation. Pour plus d’informations, consultez [solutions Office Build](../vsto/building-office-solutions.md).  
  
2.  Dans le classeur, vérifiez que vous voyez le texte suivant.  
  
     **Ce texte a été ajouté à l’aide du concepteur.**  
  
     **Ce texte a été ajouté via le code.**  
  
3.  Fermez le classeur.  
  
## <a name="clean-up-the-project"></a>Nettoyer le projet  
 Une fois que vous avez fini de développer un projet, vous devez supprimer les fichiers du dossier de sortie de génération et les paramètres de sécurité créés par le processus de génération.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Pour nettoyer le projet terminé sur votre ordinateur de développement  
  
1.  Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une fois que vous avez créé une personnalisation de base au niveau du document pour Excel, vous pouvez en apprendre plus sur la manière de développer des personnalisations dans les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les personnalisations au niveau du document : [Programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md).  
  
-   Tâches de programmation sont aux personnalisations au niveau du document pour Excel : [Solutions Excel](../vsto/excel-solutions.md).  
  
-   À l’aide du modèle objet d’Excel : [Vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md).  
  
-   Personnalisation de l’interface utilisateur d’Excel, par exemple, en ajoutant un onglet personnalisé au ruban ou en créant votre propre volet actions : [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
-   À l’aide d’objets Excel étendus fournis par les outils de développement Office dans Visual Studio pour effectuer des tâches qui ne sont pas possibles en utilisant le modèle objet Excel (par exemple, héberger des contrôles managés sur des documents et lier des contrôles Excel aux données en utilisant les formulaires Windows modèle de liaison de données) : [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md).  
  
-   Génération et débogage des personnalisations au niveau du document pour Excel : [Générer des solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement de personnalisations au niveau du document pour Excel : [Déployer une solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Solutions Excel](../vsto/excel-solutions.md)   
 [Programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md)   
 [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Générer des solutions Office](../vsto/building-office-solutions.md)   
 [Déployer une solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
