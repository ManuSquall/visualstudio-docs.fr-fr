---
title: Créer votre première personnalisation au niveau du document pour Word
description: Créer une personnalisation au niveau du document pour Microsoft Word. Les fonctionnalités que vous créez dans ce genre de solution sont disponibles uniquement quand un document spécifique est ouvert.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 71051c6255f9035079a7888fb3a4c7df2f5eab59
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827550"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Procédure pas à pas : création de votre première personnalisation au niveau du document pour Word

  Cette procédure pas à pas d'introduction vous indique comment créer une personnalisation au niveau du document pour Microsoft Office Word. Les fonctionnalités que vous créez dans ce genre de solution sont disponibles uniquement quand un document spécifique est ouvert. Vous ne pouvez pas utiliser une personnalisation au niveau du document pour apporter des apporter de modifications au niveau de l'application, comme afficher un nouvel onglet de ruban quand un document est ouvert.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d'un projet de document Word.

- Ajout de texte au document hébergé dans le concepteur Visual Studio.

- Écriture de code qui utilise le modèle objet de Word pour ajouter du texte au document personnalisé lorsqu'il est ouvert.

- Génération et exécution du projet pour le tester

- Nettoyage du projet pour supprimer les fichiers de build inutiles et les paramètres de sécurité de votre ordinateur de développement.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis

 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Créer le projet

### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Pour créer un projet de document Word dans Visual Studio

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.
::: moniker range="vs-2017"
3. Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.

4. Sous le nœud **Office/SharePoint** développé, sélectionnez le nœud **compléments VSTO** .

5. Dans la liste des modèles de projet, sélectionnez un projet de document VSTO Word.

6. Dans la zone **nom** , tapez **FirstDocumentCustomization**.

7. Cliquez sur **OK**.

8. Sélectionnez **créer un nouveau document** à partir de l' **Assistant projet Visual Studio Tools pour Office**, puis cliquez sur **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
3. Dans la boîte de dialogue **créer un nouveau projet** , sélectionnez le projet **document VSTO Word** .

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Cliquez sur **Suivant**.

5. Tapez **FirstWorkbookCustomization** dans la zone **nom** de la boîte de dialogue **configurer votre nouveau projet** , puis cliquez sur **créer**.

6. Sélectionnez **créer un nouveau document** à partir de l' **Assistant projet Visual Studio Tools pour Office**, puis cliquez sur **OK**.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet **FirstDocumentCustomization** et ajoute le document **FirstDocumentCustomization** et le fichier de code ThisDocument au projet. Le document **FirstDocumentCustomization** s’ouvre automatiquement dans le concepteur.

## <a name="close-and-reopen-the-document-in-the-designer"></a>Fermer et rouvrir le document dans le concepteur

 Si vous fermez délibérément ou accidentellement le document dans le concepteur pendant que vous développez votre projet, vous pouvez le rouvrir.

### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Pour fermer et rouvrir le document dans le concepteur

1. Fermez le document en cliquant sur le bouton **Fermer** (X) de la fenêtre du concepteur.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code **ThisDocument** , puis cliquez sur **Concepteur de vues**.

     \- ou -

     Dans **Explorateur de solutions**, double-cliquez sur le fichier de code **ThisDocument** .

## <a name="add-text-to-the-document-in-the-designer"></a>Ajouter du texte au document dans le concepteur

 Vous pouvez concevoir l'interface utilisateur de votre personnalisation en modifiant le document qui est ouvert dans le concepteur. Par exemple, vous pouvez ajouter du texte, des tableaux ou des contrôles Word. Pour plus d’informations sur l’utilisation du concepteur, consultez [projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Pour ajouter du texte à votre document à l'aide du concepteur

1. Dans le document ouvert dans le concepteur, tapez le texte suivant.

     **Ce texte a été ajouté à l'aide du concepteur.**

## <a name="add-text-to-the-document-programmatically"></a>Ajouter du texte au document par programmation

 L'étape suivante consiste à ajouter du code dans le fichier ThisDocument. Le nouveau code utilise le modèle objet de Word pour ajouter un deuxième paragraphe de texte au document. Par défaut, le fichier de code ThisDocument contient le code généré suivant :

- Une définition partielle de la classe `ThisDocument`, qui représente le modèle de programmation du document et permet d'accéder au modèle objet de Word. Pour plus d’informations, consultez [élément hôte de document](../vsto/document-host-item.md) et [vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md). Le reste de la classe `ThisDocument` est défini dans un fichier de code masqué que vous ne devez pas modifier.

- Les gestionnaires d'événements `ThisDocument_Startup` et `ThisDocument_Shutdown` . Ces gestionnaires d'événements sont appelés à l'ouverture et à la fermeture du document. Utilisez ces gestionnaires d'événements pour initialiser votre personnalisation à l'ouverture du document et pour nettoyer les ressources utilisées par votre personnalisation à la fermeture du document. Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Pour ajouter un deuxième paragraphe de texte au document à l'aide de code

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument**, puis cliquez sur **afficher le code**.

     Le fichier de code s'ouvre dans Visual Studio.

2. Remplacez le gestionnaire d'événements `ThisDocument_Startup` par le code suivant. Lorsque le document s'ouvre, ce code ajoute un deuxième paragraphe de texte au document.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs" id="Snippet1":::

    > [!NOTE]
    > Ce code utilise la valeur d'index 1 pour accéder au premier paragraphe de la propriété <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>. Bien que Visual Basic et Visual C# utilisent des tableaux basés sur 0, les limites d'index de tableau inférieures de la plupart des collections du modèle objet Word ont la valeur 1. Pour plus d’informations, consultez [écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md).

## <a name="test-the-project"></a>Tester le projet

### <a name="to-test-your-document"></a>Pour tester votre document

1. Appuyez sur **F5** pour générer et exécuter votre projet.

     Lorsque vous générez le projet, le code est compilé dans un assembly qui est associé au document. Visual Studio place une copie du document et l'assembly dans le dossier de sortie de la génération du projet, et il configure les paramètres de sécurité sur l'ordinateur de développement pour permettre l'exécution de la personnalisation. Pour plus d’informations, consultez [créer des solutions Office](../vsto/building-office-solutions.md).

2. Dans le document, vérifiez que vous voyez le texte suivant.

     **Ce texte a été ajouté à l'aide du concepteur.**

     **Ce texte a été ajouté via le code.**

3. Fermez le document.

## <a name="clean-up-the-project"></a>Nettoyer le projet

 Une fois que vous avez fini de développer un projet, vous devez supprimer les fichiers du dossier de sortie de génération et les paramètres de sécurité créés par le processus de génération.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Pour nettoyer le projet terminé sur votre ordinateur de développement

1. Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.

## <a name="next-steps"></a>Étapes suivantes

 Maintenant que vous avez créé une personnalisation de base au niveau du document pour Word, vous pouvez en apprendre plus sur la manière de développer des personnalisations dans les rubriques suivantes :

- Tâches de programmation générales que vous pouvez effectuer dans les personnalisations au niveau du document : [programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md).

- Tâches de programmation spécifiques aux personnalisations au niveau du document pour Word : [solutions Word](../vsto/word-solutions.md).

- Utilisation du modèle objet de Word : [vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md).

- Personnalisation de l’interface utilisateur de Word, par exemple, en ajoutant un onglet personnalisé au ruban ou en créant votre propre volet Actions : personnalisation de l' [interface utilisateur Office](../vsto/office-ui-customization.md).

- Utilisation d’objets Word étendus fournis par les solutions Office dans Visual Studio pour effectuer des tâches qui ne sont pas possibles en utilisant le modèle objet Word (par exemple, héberger des contrôles managés sur des documents et lier des contrôles Word à des données à l’aide du modèle de liaison de données Windows Forms) : [automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md).

- Génération et débogage des personnalisations au niveau du document pour Word : [créer des solutions Office](../vsto/building-office-solutions.md).

- Déploiement de personnalisations au niveau du document pour Word : [déployer une solution Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Solutions Word](../vsto/word-solutions.md)
- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)
- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Créer des solutions Office](../vsto/building-office-solutions.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
- [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)
