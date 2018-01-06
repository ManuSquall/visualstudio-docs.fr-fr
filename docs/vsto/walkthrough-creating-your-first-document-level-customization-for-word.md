---
title: "Procédure pas à pas : Création de votre première personnalisation au niveau du Document pour Word | Documents Microsoft"
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
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
ms.assetid: ec9f5173-0923-4aee-985a-e760e80eaae3
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6d732f16d6794fbe59dd6f67fa904fcee916ce69
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-your-first-document-level-customization-for-word"></a>Procédure pas à pas : création de votre première personnalisation au niveau du document pour Word
  Cette procédure pas à pas d'introduction vous indique comment créer une personnalisation au niveau du document pour Microsoft Office Word. Les fonctionnalités que vous créez dans ce genre de solution sont disponibles uniquement quand un document spécifique est ouvert. Vous ne pouvez pas utiliser une personnalisation au niveau du document pour apporter des apporter de modifications au niveau de l'application, comme afficher un nouvel onglet de ruban quand un document est ouvert.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet de document Word.  
  
-   Ajout de texte au document hébergé dans le concepteur Visual Studio.  
  
-   Écriture de code qui utilise le modèle objet de Word pour ajouter du texte au document personnalisé lorsqu'il est ouvert.  
  
-   Génération et exécution du projet pour le tester  
  
-   Nettoyage du projet pour supprimer les fichiers de build inutiles et les paramètres de sécurité de votre ordinateur de développement.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>Création du projet  
  
#### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Pour créer un projet de document Word dans Visual Studio  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.  
  
4.  Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .  
  
5.  Dans la liste des modèles de projet, sélectionnez un projet de document VSTO Word.  
  
6.  Dans le **nom** , tapez **FirstDocumentCustomization**.  
  
7.  Cliquez sur **OK**.  
  
     L' **Assistant Projet Visual Studio Tools pour Office** s'ouvre.  
  
8.  Sélectionnez **créer un nouveau document**, puis cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]crée le **FirstDocumentCustomization** le projet, puis ajoute le **FirstDocumentCustomization** document et le fichier de code ThisDocument au projet. Le **FirstDocumentCustomization** document est ouvert automatiquement dans le concepteur.  
  
## <a name="closing-and-reopening-the-document-in-the-designer"></a>Fermeture et réouverture du document dans le concepteur  
 Si vous fermez délibérément ou accidentellement le document dans le concepteur pendant que vous développez votre projet, vous pouvez le rouvrir.  
  
#### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Pour fermer et rouvrir le document dans le concepteur  
  
1.  Fermer le document en cliquant sur le **fermer** bouton (X) de la fenêtre du concepteur.  
  
2.  Dans **l’Explorateur de solutions**, avec le bouton droit le **ThisDocument** fichier de code, puis cliquez sur **Concepteur de vue**.  
  
     \- ou -  
  
     Dans **l’Explorateur de solutions**, double-cliquez sur le **ThisDocument** fichier de code.  
  
## <a name="adding-text-to-the-document-in-the-designer"></a>Ajout de texte au document dans le concepteur  
 Vous pouvez concevoir l'interface utilisateur de votre personnalisation en modifiant le document qui est ouvert dans le concepteur. Par exemple, vous pouvez ajouter du texte, des tableaux ou des contrôles Word. Pour plus d’informations sur l’utilisation du concepteur, consultez [les projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Pour ajouter du texte à votre document à l'aide du concepteur  
  
1.  Dans le document ouvert dans le concepteur, tapez le texte suivant.  
  
     **Ce texte a été ajouté à l’aide du concepteur.**  
  
## <a name="adding-text-to-the-document-programmatically"></a>Ajout de texte au document par programmation  
 L'étape suivante consiste à ajouter du code dans le fichier ThisDocument. Le nouveau code utilise le modèle objet de Word pour ajouter un deuxième paragraphe de texte au document. Par défaut, le fichier de code ThisDocument contient le code généré suivant :  
  
-   Une définition partielle de la classe `ThisDocument`, qui représente le modèle de programmation du document et permet d'accéder au modèle objet de Word. Pour plus d’informations, consultez [élément hôte de Document](../vsto/document-host-item.md) et [présentation du modèle objet de Word](../vsto/word-object-model-overview.md). Le reste de la classe `ThisDocument` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `ThisDocument_Startup` et `ThisDocument_Shutdown`. Ces gestionnaires d'événements sont appelés à l'ouverture et à la fermeture du document. Utilisez ces gestionnaires d'événements pour initialiser votre personnalisation à l'ouverture du document et pour nettoyer les ressources utilisées par votre personnalisation à la fermeture du document. Pour plus d'informations, consultez [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Pour ajouter un deuxième paragraphe de texte au document à l'aide de code  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **ThisDocument**, puis cliquez sur **afficher le Code**.  
  
     Le fichier de code s'ouvre dans Visual Studio.  
  
2.  Remplacez le gestionnaire d'événements `ThisDocument_Startup` par le code suivant. Lorsque le document s'ouvre, ce code ajoute un deuxième paragraphe de texte au document.  
  
     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]  
  
    > [!NOTE]  
    >  Ce code utilise la valeur d'index 1 pour accéder au premier paragraphe de la propriété <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>. Bien que Visual Basic et Visual C# utilisent des tableaux basés sur 0, les limites d’index de tableau inférieures de la plupart des collections du modèle objet Word ont la valeur 1. Pour plus d'informations, consultez [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="testing-the-project"></a>Test du projet  
  
#### <a name="to-test-your-document"></a>Pour tester votre document  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet.  
  
     Lorsque vous générez le projet, le code est compilé dans un assembly qui est associé au document. Visual Studio place une copie du document et l’assembly dans le dossier de sortie de la génération du projet, et il configure les paramètres de sécurité sur l’ordinateur de développement pour permettre l’exécution de la personnalisation. Pour plus d’informations, consultez [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
2.  Dans le document, vérifiez que vous voyez le texte suivant.  
  
     **Ce texte a été ajouté à l’aide du concepteur.**  
  
     **Ce texte a été ajouté via le code.**  
  
3.  Fermez le document.  
  
## <a name="cleaning-up-the-project"></a>Nettoyage du projet  
 Une fois que vous avez fini de développer un projet, vous devez supprimer les fichiers du dossier de sortie de génération et les paramètres de sécurité créés par le processus de génération.  
  
#### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Pour nettoyer le projet terminé sur votre ordinateur de développement  
  
1.  Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez créé une personnalisation de base au niveau du document pour Word, vous pouvez en apprendre plus sur la manière de développer des personnalisations dans les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les personnalisations au niveau du document : [programmation de personnalisations au niveau du Document](../vsto/programming-document-level-customizations.md).  
  
-   Tâches de programmation sont aux personnalisations au niveau du document pour Word : [Solutions Word](../vsto/word-solutions.md).  
  
-   À l’aide du modèle objet de Word : [présentation du modèle objet de Word](../vsto/word-object-model-overview.md).  
  
-   Personnalisation de l’interface utilisateur de Word, par exemple, en ajoutant un onglet personnalisé au ruban ou en créant votre propre volet actions : [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
-   À l’aide d’objets Word étendus fournis par les solutions Office dans Visual Studio pour effectuer des tâches qui ne sont pas possibles en utilisant le modèle objet Word (par exemple, héberger des contrôles managés sur des documents et lier des contrôles Word aux données en utilisant les données Windows Forms modèle de liaison) : [automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Génération et débogage des personnalisations au niveau du document pour Word : [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement de personnalisations au niveau du document pour Word : [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du développement de Solutions Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Solutions Word](../vsto/word-solutions.md)   
 [Programmation des personnalisations au niveau du Document](../vsto/programming-document-level-customizations.md)   
 [Vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md)   
 [Automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Génération de Solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  