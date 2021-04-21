---
title: 'Procédure pas à pas : créer votre premier complément VSTO pour Word'
description: Créez un complément de niveau application pour Microsoft Word. Cette fonctionnalité est disponible pour l’application elle-même, quels que soient les documents ouverts.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd3509ab674faa220ed7bbea15a9762f52b1a525
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828278"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>Procédure pas à pas : créer votre premier complément VSTO pour Word
  Cette première procédure pas à pas montre comment créer un complément VSTO pour Microsoft Office Word. Les fonctionnalités que vous créez dans ce type de solution sont accessibles à l'application, quels que soient les documents ouverts.

 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d'un projet de complément VSTO Word

- Écriture d'un code qui utilise le modèle objet de Word pour ajouter du texte à un document quand il est enregistré

- Génération et exécution du projet pour le tester

- Nettoyage du projet terminé, pour que le complément VSTO ne s’exécute plus automatiquement sur votre ordinateur de développement

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Créer le projet

### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Pour créer un projet de complément VSTO Word dans Visual Studio

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3. Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.

4. Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .

5. Dans la liste des modèles de projet, sélectionnez un projet de complément VSTO Word.

6. Dans la zone **nom** , tapez **premiercomplémentexcel**.

7. Cliquez sur **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet **premiercomplémentexcel** et ouvre le fichier de code ThisAddIn dans l’éditeur.

## <a name="write-code-to-add-text-to-the-saved-document"></a>Écrire du code pour ajouter du texte au document enregistré
 L'étape suivante consiste à ajouter du code au fichier de code ThisAddIn. Le nouveau code utilise le modèle objet de Word pour ajouter du texte réutilisable dans chaque document enregistré. Par défaut, le fichier de code ThisAddIn contient le code généré suivant :

- Une définition partielle de la classe `ThisAddIn` . Cette classe fournit un point d'entrée pour votre code et offre un accès au modèle objet de Word. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md). Le reste de la `ThisAddIn` classe est défini dans un fichier de code masqué que vous ne devez pas modifier.

- Les gestionnaires d'événements `ThisAddIn_Startup` et `ThisAddIn_Shutdown` . Ces gestionnaires d’événements sont appelés quand Word charge et décharge votre complément VSTO. Utilisez ces gestionnaires d'événements pour initialiser votre complément VSTO quand il est chargé, ainsi que pour nettoyer les ressources utilisées par votre complément VSTO quand il est déchargé. Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Pour ajouter un paragraphe de texte au document enregistré

1. Dans le fichier de code ThisAddIn, ajoutez le code suivant à la classe `ThisAddIn` . Le nouveau code définit un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>, qui est déclenché quand un document est enregistré.

    Quand l'utilisateur enregistre un document, le gestionnaire d'événements ajoute le nouveau texte au début du document.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs" id="Snippet1":::

   > [!NOTE]
   > Ce code utilise une valeur d’index 1 pour accéder au premier paragraphe de la collection <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A>. Bien que Visual Basic et Visual C# utilisent des tableaux basés sur 0, les limites d'index de tableau inférieures de la plupart des collections du modèle objet Word ont la valeur 1. Pour plus d’informations, consultez [écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md).

2. Si vous utilisez C#, ajoutez le code requis suivant au gestionnaire d'événements `ThisAddIn_Startup` . Ce code permet de connecter le gestionnaire d'événements `Application_DocumentBeforeSave` à l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs" id="Snippet2":::

   Pour modifier le document quand il est enregistré, les exemples de code précédents utilisent les objets suivants :

- Le champ `Application` de la classe `ThisAddIn` . Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.Word.Application>, qui représente l'instance actuelle de Word.

- Le paramètre `Doc` du gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . Le paramètre `Doc` est un objet <xref:Microsoft.Office.Interop.Word.Document> qui représente le document enregistré. Pour plus d’informations, consultez [vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md).

## <a name="test-the-project"></a>Tester le projet

### <a name="to-test-the-project"></a>Pour tester le projet

1. Appuyez sur **F5** pour générer et exécuter votre projet.

     Quand vous générez le projet, le code est compilé dans un assembly qui est inclus dans le dossier de sortie de la génération du projet. Visual Studio crée également un jeu d’entrées du Registre qui permet à Word de détecter et de charger le complément VSTO, et il configure les paramètres de sécurité de l’ordinateur de développement pour permettre au complément VSTO de s’exécuter. Pour plus d’informations, consultez [créer des solutions Office](../vsto/building-office-solutions.md).

2. Dans Word, enregistrez le document actif.

3. Vérifiez que le texte suivant est ajouté au document.

     **Ce texte a été ajouté via le code.**

4. Fermez Word.

## <a name="clean-up-the-project"></a>Nettoyer le projet
 Une fois que vous avez terminé de développer un projet, supprimez l'assembly du complément VSTO, les entrées de Registre et les paramètres de sécurité de votre ordinateur de développement. Sinon, le complément VSTO s'exécutera chaque fois que vous ouvrirez Word sur votre ordinateur de développement.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Pour nettoyer le projet terminé sur votre ordinateur de développement

1. Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.

## <a name="next-steps"></a>Étapes suivantes
 Maintenant que vous avez créé un complément VSTO de base pour Word, vous pouvez perfectionner votre connaissance du développement des compléments VSTO en consultant les rubriques suivantes :

- Tâches de programmation générales que vous pouvez effectuer dans les compléments VSTO : [programmez les compléments VSTO](../vsto/programming-vsto-add-ins.md).

- Tâches de programmation spécifiques aux compléments VSTO Word : [solutions Word](../vsto/word-solutions.md).

- Utilisation du modèle objet de Word : [vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md).

- Personnalisation de l’interface utilisateur de Word, par exemple, en ajoutant un onglet personnalisé au ruban ou en créant votre propre volet des tâches personnalisé : personnalisation de l' [interface utilisateur Office](../vsto/office-ui-customization.md).

- Génération et débogage de compléments VSTO pour Word : [créer des solutions Office](../vsto/building-office-solutions.md).

- Déploiement de compléments VSTO pour Word : [déployer une solution Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Solutions Word](../vsto/word-solutions.md)
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Créer des solutions Office](../vsto/building-office-solutions.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
- [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)
