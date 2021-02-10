---
title: Créer des zones de formulaire Outlook
description: Découvrez comment vous pouvez utiliser des zones de formulaire pour personnaliser les formulaires Microsoft Outlook afin de faciliter la conception, le développement et le débogage des zones de formulaire.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ba2c4412b344a37e1b1db74cdddea8c5b60b69d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947891"
---
# <a name="create-outlook-form-regions"></a>Créer des zones de formulaire Outlook
  Vous pouvez utiliser des zones de formulaire pour personnaliser des formulaires Microsoft Office Outlook. Visual Studio fournit des outils avancés qui simplifient la conception, le développement et le débogage des zones de formulaire.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Cette rubrique fournit les informations suivantes :

- [Avantages de l’utilisation des zones de formulaire](#Enhance)

- [Ajouter une zone de formulaire Outlook à votre projet](#Adding)

- [Utiliser le concepteur de zones de formulaire](#UsingFormRegionDesigner)

- [Utiliser une zone de formulaire conçue dans Outlook](#UsingFormRegionDesignedOutlook)

- [Ajouter du code personnalisé à une zone de formulaire](#AddingCustomCode)

- [Créer le projet](#Building)

- [Déboguer une zone de formulaire](#Debugging)

- [Déployer une zone de formulaire](#Deploying)

## <a name="advantages-of-using-form-regions"></a><a name="Enhance"></a> Avantages de l’utilisation des zones de formulaire
 Les zones de formulaire offrent de nombreuses améliorations par rapport au développement de formulaires Outlook classiques :

- personnalisation de la page par défaut de n'importe quel formulaire standard,

- ajout d'un maximum de 12 pages supplémentaires à n'importe quel formulaire standard,

- remplacement ou amélioration de n'importe quel formulaire standard,

- affichage de l'interface utilisateur personnalisée dans le volet de lecture et dans les inspecteurs.

  Pour plus d’informations, consultez [personnaliser les pages de formulaire et les zones de formulaire](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions).

## <a name="add-an-outlook-form-region-to-your-project"></a><a name="Adding"></a> Ajouter une zone de formulaire Outlook à votre projet
 Vous pouvez utiliser l’Assistant **nouvelle zone de formulaire Outlook** pour concevoir une nouvelle zone de formulaire ou importer une zone de formulaire conçue dans Outlook. En outre, si vous disposez d'une zone de formulaire que vous avez utilisée dans un autre projet de complément VSTO Outlook, vous pouvez réutiliser votre zone de formulaire existante.

### <a name="create-a-new-form-region-by-using-the-wizard"></a><a name="CreatingFormRegion"></a> Créer une zone de formulaire à l’aide de l’Assistant
 Pour créer une zone de formulaire, ajoutez un élément de **zone de formulaire Outlook** à un projet de complément VSTO Outlook. Cette action démarre l’Assistant **nouvelle zone de formulaire Outlook** .

 Utilisez cet Assistant pour indiquer si vous voulez concevoir une nouvelle zone de formulaire ou importer une zone de formulaire conçue dans Outlook. Pour plus d’informations sur la conception d’une nouvelle zone de formulaire, consultez [utiliser le concepteur de zones de formulaire](#UsingFormRegionDesigner). Pour plus d’informations sur l’utilisation d’une zone de formulaire conçue dans Outlook, consultez [Importer une zone de formulaire conçue dans Outlook](#UsingFormRegionDesignedOutlook).

 Utilisez l'Assistant pour spécifier le type de zone de formulaire que vous souhaitez créer. Le tableau suivant décrit chaque type de zone de formulaire.

|Type de région|Description|
|-----------------|-----------------|
|Separate|Ajoute la zone de formulaire en tant que nouvelle page dans un formulaire Outlook.|
|Adjacent|Ajoute la zone de formulaire au bas de la page par défaut d'un formulaire Outlook.|
|Remplacement|Ajoute la zone de formulaire en tant que nouvelle page qui remplace la page par défaut d'un formulaire Outlook.|
|Remplacement global|Remplace l'intégralité du formulaire Outlook par la zone de formulaire.|

 Vous pouvez également utiliser l'Assistant pour spécifier les conditions d'affichage et sélectionner le type de formulaire à étendre. Pour plus d’informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Les sélections que vous effectuez dans l'Assistant affectent les options disponibles dans les autres pages de l'Assistant. Par exemple, si vous sélectionnez l’option **adjacente** ou **séparer** dans la page **créer une nouvelle zone de formulaire Outlook** , les champs **titre** et **Description** ne sont pas disponibles dans la page **fournir un texte descriptif et sélectionnez vos préférences d’affichage** . Cela tient au fait qu'Outlook n'utilise pas ces champs pour afficher une zone de formulaire adjacente ou distincte.

#### <a name="form-region-files"></a>Fichiers de zone de formulaire
 Lorsque vous terminez l’Assistant **nouvelle zone de formulaire Outlook** , Visual Studio ajoute automatiquement les fichiers suivants à votre projet :

- Un fichier de code de zone de formulaire. Ce fichier porte le nom que vous spécifiez pour l’élément **zone de formulaire Outlook** dans la boîte de dialogue **Ajouter un nouvel élément** . Ajoutez à ce fichier du code pour gérer les événements de zone de formulaire.

- Un fichier de code du Concepteur de zones de formulaire. Ce fichier contient le code généré par le Concepteur de zones de formulaire et ne doit pas être modifié directement.

- Fichier de stockage de formulaire Outlook (*. OFS*).

    > [!NOTE]
    > Ce fichier est ajouté uniquement au projet si vous importez une zone de formulaire conçue dans Outlook.

#### <a name="form-region-factory-class"></a>Classe de fabrique de zones de formulaire
 Le fichier de code de la zone de formulaire contient une classe partielle qui implémente l'interface <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory>. Il s'agit de la classe de fabrique de zones de formulaire. Cette classe est chargée de créer de nouvelles instances de la zone de formulaire.

 Vous pouvez trouver cette classe en développant la région de **fabrique de zones de formulaire** .

 L’Assistant **nouvelle zone de formulaire Outlook** ajoute des attributs à cette classe qui spécifient le nom interne de la zone de formulaire et les classes de message qui affichent la zone de formulaire. Vous pouvez modifier ces attributs manuellement une fois que le fichier a été ajouté au projet.

 La plus grande partie de la classe de fabrique de zones de formulaire est implémentée dans le fichier du Concepteur de zones de formulaire. Toutefois, le gestionnaire d'événements `FormRegionInitializing` est exposé dans le fichier de code de la zone de formulaire. Vous pouvez utiliser ce gestionnaire d'événements pour spécifier si Outlook doit afficher la zone de formulaire. Pour plus d’informations, consultez [gérer les événements de zone de formulaire](#HandlingFormRegionEvents).

### <a name="add-an-existing-form-region-to-your-project"></a><a name="AddingExistingFormRegion"></a> Ajouter une zone de formulaire existante à votre projet
 Si vous disposez d'une zone de formulaire Outlook que vous avez utilisée dans un autre projet Outlook, vous pouvez la réutiliser dans votre projet de complément VSTO Outlook actuel à l'aide de la boîte de dialogue **Ajouter un élément existant** .

 La zone de formulaire existante doit avoir un fichier de code (*. vb* ou *. cs*); vous ne pouvez pas ajouter de fichiers de stockage de formulaire Outlook (*. OFS*) à l’aide de la boîte de dialogue **Ajouter un élément existant** . Toutefois, vous pouvez créer une nouvelle zone de formulaire en important un fichier de stockage de formulaire Outlook. Pour plus d’informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

## <a name="use-the-form-region-designer"></a><a name="UsingFormRegionDesigner"></a> Utiliser le concepteur de zones de formulaire
 Le Concepteur de zones de formulaire vous aide à concevoir la disposition et l'apparence d'une zone de formulaire. Vous pouvez faire glisser des contrôles managés sur la surface du concepteur, double-cliquer sur des contrôles pour ouvrir des gestionnaires d’événements et définir des propriétés dans la fenêtre **Propriétés** .

> [!NOTE]
> Vous pouvez trouver des propriétés qui affectent la façon dont la zone de formulaire apparaît dans Outlook sous le nœud **manifeste** dans la fenêtre **Propriétés** .

 Le concepteur de zones de formulaire est disponible uniquement si vous sélectionnez **concevoir une nouvelle zone de formulaire** dans la page **Sélectionnez la méthode de création de la zone de formulaire** de l’Assistant **nouvelle zone de formulaire Outlook** .

 Il existe trois façons d'ouvrir le Concepteur de zones de formulaire :

- Dans **Explorateur de solutions**, double-cliquez sur le fichier de code de la zone de formulaire.

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code de la zone de formulaire, puis cliquez sur **Concepteur de vues**.

- Dans **Explorateur de solutions**, sélectionnez le fichier de code de la zone de formulaire, puis, dans le menu **affichage** , cliquez sur **Concepteur**.

  Le Concepteur de zones de formulaire prend en charge uniquement les contrôles managés. Vous ne pouvez pas ajouter de contrôles Outlook natifs.

## <a name="import-a-form-region-designed-in-outlook"></a><a name="UsingFormRegionDesignedOutlook"></a> Importer une zone de formulaire conçue dans Outlook
 Quand vous concevez une zone de formulaire dans Outlook, vous pouvez lui ajouter des contrôles Outlook natifs. Les contrôles Outlook natifs vous permettent de créer une liaison avec les données Outlook au moment du design. Toutefois, vous ne pouvez pas utiliser ensuite le Concepteur de zones de formulaire pour ajouter des contrôles managés ou modifier la conception de la zone de formulaire.

 Vous pouvez importer des zones de formulaire dans un projet de complément VSTO Outlook à l’aide de l’Assistant **nouvelle zone de formulaire Outlook** . Dans la page **Sélectionnez la méthode de création de la zone de formulaire** , sélectionnez **Importer un fichier de stockage de formulaire Outlook (. OFS)**. Vous pouvez ensuite accéder à l’emplacement d’un fichier de stockage de formulaire Outlook (*. OFS*). (Outlook enregistre les zones de formulaire en tant que fichiers *. OFS* .)

 L’Assistant **nouvelle zone de formulaire Outlook** copie le fichier *. OFS* dans le répertoire du projet et ajoute des références de contrôle au fichier du concepteur de zones de formulaire. Vous pouvez ensuite gérer les événements de contrôle dans le fichier de code de région de formulaire.

 Pour gérer des événements dans un projet Visual Basic, sélectionnez un événement dans la liste des noms de méthodes en haut de l'éditeur de code.

 Pour gérer des événements dans un projet C#, abonnez-vous aux événements de contrôle dans la méthode <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements &#40;Guide de programmation du&#35; C&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).

 Vous pouvez modifier les propriétés des zones de formulaire dans la méthode `InitializeManifest` de la classe de fabrique de zones de formulaire.

> [!NOTE]
> Pour importer une zone de formulaire, vous devez travailler dans un projet qui cible la version d'Outlook que vous avez installée sur l'ordinateur de développement. Par exemple, si vous avez installé Outlook 2010, l’importation d’une zone de formulaire ne fonctionnera que dans un projet créé à l’aide du modèle **de projet de complément Outlook 2010** .

### <a name="update-an-imported-form-regions-design"></a>Mettre à jour la conception d’une zone de formulaire importée
 Vous pouvez ajouter, supprimer ou modifier des contrôles dans la zone de formulaire. Avant cela, sauvegardez tout le code que vous avez ajouté au fichier de code de la zone de formulaire. Ensuite, ouvrez le fichier *. OFS* dans Outlook, modifiez la zone de formulaire, puis enregistrez les modifications. Utilisez l’Assistant **nouvelle zone de formulaire Outlook** pour importer le fichier *. OFS* modifié. Vous pouvez ensuite coller votre code dans le fichier de code de la nouvelle zone de formulaire.

## <a name="add-custom-code-to-a-form-region"></a><a name="AddingCustomCode"></a> Ajouter du code personnalisé à une zone de formulaire
 L'espace de noms <xref:Microsoft.Office.Tools.Outlook> vous donne accès aux classes qui représentent la zone de formulaire, à l'élément Outlook qui affiche la zone de formulaire et à d'autres éléments utiles. L’élément **zone de formulaire Outlook** ajoute automatiquement une référence à cet assembly dans le projet et insère l’instruction **using** ou **Imports** appropriée en haut du fichier de code de la zone de formulaire.

 Vous pouvez utiliser des classes, des méthodes et des propriétés dans l’espace de noms `Microsoft.Office.Interop.Outlook` pour accomplir la plupart de vos tâches de programmation Outlook. Pour plus d’informations sur le modèle objet Outlook, consultez [vue d’ensemble du modèle objet Outlook](../vsto/outlook-object-model-overview.md). Pour obtenir des exemples de tâches classiques qui utilisent le modèle objet Outlook, consultez [solutions Outlook](../vsto/outlook-solutions.md).

### <a name="handle-form-region-events"></a><a name="HandlingFormRegionEvents"></a> Gérer les événements de zone de formulaire
 L’élément **zone de formulaire Outlook** ajoute automatiquement les trois gestionnaires d’événements suivants au fichier de code de la zone de formulaire.

|Événement|Description|
|-----------|-----------------|
|FormRegionInitializing|Se produit avant l'initialisation de la zone de formulaire. Vous pouvez vérifier des conditions dans ce gestionnaire d'événements pour déterminer si Outlook doit afficher la zone de formulaire. Pour plus d’informations, consultez [Comment : empêcher Outlook d’afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|
|FormRegionShowing|Se produit après la création d'une instance de la zone de formulaire, mais avant l'affichage de la zone de formulaire.|
|FormRegionClosed|Se produit avant la fermeture de la zone de formulaire.|

## <a name="build-the-project"></a><a name="Building"></a> Générer le projet
 Quand vous générez un projet de complément VSTO Outlook qui contient une zone de formulaire, Visual Studio ajoute les informations suivantes dans le Registre :

- une clé pour chaque classe de message associée à une ou plusieurs zones de formulaire,

- une entrée pour chaque zone de formulaire et une valeur associée représentant le nom du complément VSTO Outlook.

  Outlook utilise ces informations pour charger les zones de formulaire.

## <a name="debug-a-form-region"></a><a name="Debugging"></a> Déboguer une zone de formulaire
 Pour déboguer un complément VSTO Outlook contenant une zone de formulaire, procédez comme pour tout autre projet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Quand vous démarrez le débogueur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Visual Studio démarre automatiquement Outlook.

 Pour afficher la zone de formulaire, vous devez ouvrir l'élément Outlook approprié. Par exemple, si une zone de formulaire adjacente est ajoutée au bas d'un élément de messagerie, ouvrez un élément de messagerie.

## <a name="deploy-a-form-region"></a><a name="Deploying"></a> Déployer une zone de formulaire
 Les zones de formulaire sont déployées automatiquement avec le complément VSTO Outlook associé. Il est donc inutile d'exécuter des tâches spéciales pour déployer une zone de formulaire. Pour plus d’informations sur le déploiement de compléments VSTO, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Instructions pour la création de zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Fournit des informations pouvant vous aider à optimiser vos zones de formulaire et à éviter d'éventuels problèmes.|
|[Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Montre comment créer une zone de formulaire pour étendre un formulaire Microsoft Office Outlook standard ou personnalisé à l’aide de l’Assistant **nouvelle zone de formulaire Outlook** .|
|[Associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Explique comment spécifier les éléments Microsoft Office Outlook qui doivent afficher une zone de formulaire en associant cette dernière à la classe de message de chaque élément.|
|[Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)|Montre comment concevoir une zone de formulaire personnalisée qui apparaît en tant que nouvelle page dans la fenêtre Inspecteur d'un élément de contact.|
|[Procédure pas à pas : importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Montre comment concevoir une zone de formulaire dans Microsoft Office Outlook, puis importer la zone de formulaire dans un projet de complément VSTO Outlook à l’aide de l’Assistant **nouvelle zone de formulaire Outlook** .|
|[Accéder à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)|Explique comment écrire du code pour afficher, masquer ou modifier des contrôles dans une zone de formulaire, et comment permettre aux utilisateurs d'exécuter le code à partir d'autres zones de votre projet à l'aide de la classe `Globals`.|
|[Comment : empêcher Outlook d’afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Montre comment empêcher Microsoft Office Outlook d'afficher une zone de formulaire pour un élément particulier.|
|Montre comment accéder à l'élément Outlook dans lequel une zone de formulaire apparaît.|
|[Actions personnalisées dans les zones de formulaire Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|Explique comment permettre aux utilisateurs de répondre à un élément Outlook.|
