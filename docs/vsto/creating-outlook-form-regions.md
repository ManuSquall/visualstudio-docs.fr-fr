---
title: "Cr&#233;ation de zones de formulaire Outlook | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "zones de formulaire (développement Office dans Visual Studio)"
  - "zones de formulaire (développement Office dans Visual Studio), créer"
  - "Outlook (développement Office dans Visual Studio), zones de formulaire"
ms.assetid: a8005641-cc8b-4e07-8dca-294327cdc8d4
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Cr&#233;ation de zones de formulaire Outlook
  Vous pouvez utiliser des zones de formulaire pour personnaliser des formulaires Microsoft Office Outlook.  Visual Studio fournit des outils avancés qui simplifient la conception, le développement et le débogage des zones de formulaire.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Cette rubrique fournit les informations suivantes :  
  
-   [Avantages de l'utilisation des zones de formulaire](#Enhance)  
  
-   [Ajout d'une zone de formulaire Outlook à un projet](#Adding)  
  
-   [Utilisation du Concepteur de zones de formulaire](#UsingFormRegionDesigner)  
  
-   [Utilisation d'une zone de formulaire conçue dans Outlook](#UsingFormRegionDesignedOutlook)  
  
-   [Ajout d'un code personnalisé à une zone de formulaire](#AddingCustomCode)  
  
-   [Génération du projet](#Building)  
  
-   [Débogage d'une zone de formulaire](#Debugging)  
  
-   [Déploiement d'une zone de formulaire](#Deploying)  
  
##  <a name="Enhance"></a> Avantages de l'utilisation des zones de formulaire  
 Les zones de formulaire offrent de nombreuses améliorations par rapport au développement de formulaires Outlook classiques :  
  
-   personnalisation de la page par défaut de n'importe quel formulaire standard,  
  
-   ajout d'un maximum de 12 pages supplémentaires à n'importe quel formulaire standard,  
  
-   remplacement ou amélioration de n'importe quel formulaire standard,  
  
-   affichage de l'interface utilisateur personnalisée dans le volet de lecture et dans les inspecteurs.  
  
 Pour plus d'informations, consultez [Personnalisation des pages et des zones de formulaire](HV10038632).  
  
##  <a name="Adding"></a> Ajout d'une zone de formulaire Outlook à un projet  
 Vous pouvez utiliser l'Assistant **Nouvelle zone de formulaire Outlook** pour concevoir une nouvelle zone de formulaire ou importer une zone de formulaire conçue dans Outlook.  En outre, si vous disposez d'une zone de formulaire que vous avez utilisée dans un autre projet de complément VSTO Outlook, vous pouvez réutiliser votre zone de formulaire existante.  
  
###  <a name="CreatingFormRegion"></a> Création d'une zone de formulaire à l'aide de l'Assistant  
 Pour créer une zone de formulaire, ajoutez un élément **Zone de formulaire Outlook** à un projet de complément VSTO Outlook.  Cela démarre l'Assistant **Nouvelle zone de formulaire Outlook**.  
  
 Utilisez cet Assistant pour indiquer si vous voulez concevoir une nouvelle zone de formulaire ou importer une zone de formulaire conçue dans Outlook.  Pour plus d'informations sur la conception d'une zone de formulaire, consultez [Utilisation du Concepteur de zones de formulaire](#UsingFormRegionDesigner).  Pour plus d'informations sur l'utilisation d'une zone de formulaire conçue dans Outlook, consultez [Importation d'une zone de formulaire conçue dans Outlook](#UsingFormRegionDesignedOutlook).  
  
 Utilisez l'Assistant pour spécifier le type de zone de formulaire que vous souhaitez créer.  Le tableau suivant décrit chaque type de zone de formulaire.  
  
|Type de zone|Description|  
|------------------|-----------------|  
|Séparer|Ajoute la zone de formulaire en tant que nouvelle page dans un formulaire Outlook.|  
|Adjacent|Ajoute la zone de formulaire au bas de la page par défaut d'un formulaire Outlook.|  
|Replacement|Ajoute la zone de formulaire en tant que nouvelle page qui remplace la page par défaut d'un formulaire Outlook.|  
|Remplacement global|Remplace l'intégralité du formulaire Outlook par la zone de formulaire.|  
  
 Vous pouvez également utiliser l'Assistant pour spécifier les conditions d'affichage et sélectionner le type de formulaire à étendre.  Pour plus d'informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Les sélections que vous effectuez dans l'Assistant affectent les options disponibles dans les autres pages de l'Assistant.  Par exemple, si vous sélectionnez **Adjacent** ou **Séparer** dans la page **Créer une nouvelle zone de formulaire Outlook**, les champs **Titre** et **Description** ne sont pas disponibles dans la page **Fournissez un texte descriptif et sélectionnez vos préférences d'affichage**.  Cela tient au fait qu'Outlook n'utilise pas ces champs pour afficher une zone de formulaire adjacente ou distincte.  
  
#### Fichiers de zone de formulaire  
 Quand vous terminez l'Assistant **Nouvelle zone de formulaire Outlook**, Visual Studio ajoute automatiquement les fichiers suivants à votre projet :  
  
-   Un fichier de code de zone de formulaire.  Ce fichier porte le nom que vous spécifiez pour l'élément **Zone de formulaire Outlook** dans la boîte de dialogue **Ajouter un nouvel élément**.  Ajoutez à ce fichier du code pour gérer les événements de zone de formulaire.  
  
-   Un fichier de code du Concepteur de zones de formulaire.  Ce fichier contient le code généré par le Concepteur de zones de formulaire et ne doit pas être modifié directement.  
  
-   Un fichier de stockage de formulaire Outlook \(.ofs\).  
  
    > [!NOTE]  
    >  Ce fichier est ajouté uniquement au projet si vous importez une zone de formulaire conçue dans Outlook.  
  
#### Classe de fabrique de zones de formulaire  
 Le fichier de code de la zone de formulaire contient une classe partielle qui implémente l'interface <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory>.  Il s'agit de la classe de fabrique de zones de formulaire.  Cette classe est chargée de créer de nouvelles instances de la zone de formulaire.  
  
 Pour trouver cette classe, développez la zone **Fabrique de zones de formulaire**.  
  
 L'Assistant **Nouvelle zone de formulaire Outlook** ajoute des attributs à cette classe qui spécifient le nom interne de la zone de formulaire et les classes de message qui affichent la zone de formulaire.  Vous pouvez modifier ces attributs manuellement une fois que le fichier a été ajouté au projet.  
  
 La plus grande partie de la classe de fabrique de zones de formulaire est implémentée dans le fichier du Concepteur de zones de formulaire.  Toutefois, le gestionnaire d'événements `FormRegionInitializing` est exposé dans le fichier de code de la zone de formulaire.  Vous pouvez utiliser ce gestionnaire d'événements pour spécifier si Outlook doit afficher la zone de formulaire.  Pour plus d'informations, consultez [Gestion des événements de la zone de formulaire](#HandlingFormRegionEvents).  
  
###  <a name="AddingExistingFormRegion"></a> Ajout d'une zone de formulaire existante à un projet  
 Si vous disposez d'une zone de formulaire Outlook que vous avez utilisée dans un autre projet Outlook, vous pouvez la réutiliser dans votre projet de complément VSTO Outlook actuel à l'aide de la boîte de dialogue **Ajouter un élément existant**.  
  
 La zone de formulaire existante doit posséder un fichier de code \(.vb ou .cs\). Vous ne pouvez pas ajouter de fichiers de stockage de formulaire Outlook \(.ofs\) à l'aide de la boîte de dialogue **Ajouter un élément existant**.  Toutefois, vous pouvez créer une nouvelle zone de formulaire en important un fichier de stockage de formulaire Outlook.  Pour plus d'informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
##  <a name="UsingFormRegionDesigner"></a> Utilisation du Concepteur de zones de formulaire  
 Le Concepteur de zones de formulaire vous aide à concevoir la disposition et l'apparence d'une zone de formulaire.  Vous pouvez faire glisser des contrôles managés dans l'aire du concepteur, double\-cliquer sur les contrôles pour ouvrir des gestionnaires d'événements et définir des propriétés dans la fenêtre **Propriétés**.  
  
> [!NOTE]  
>  Les propriétés qui affectent la façon dont la zone de formulaire apparaît dans Outlook figurent sous le nœud **Manifeste** de la fenêtre **Propriétés**.  
  
 Le Concepteur de zones de formulaire est disponible uniquement si vous sélectionnez **Créer une nouvelle zone de formulaire** dans la page **Sélectionnez la méthode de création de la zone de formulaire** de l'Assistant **Nouvelle zone de formulaire Outlook**.  
  
 Il existe trois façons d'ouvrir le Concepteur de zones de formulaire :  
  
-   Dans l'**Explorateur de solutions**, double\-cliquez sur le fichier de code de zone de formulaire.  
  
-   Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code de zone de formulaire, puis cliquez sur **Concepteur de vues**.  
  
-   Dans l'**Explorateur de solutions**, sélectionnez le fichier de code de zone de formulaire, puis, dans le menu **Affichage**, cliquez sur **Concepteur**.  
  
 Le Concepteur de zones de formulaire prend en charge uniquement les contrôles managés.  Vous ne pouvez pas ajouter de contrôles Outlook natifs.  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> Importation d'une zone de formulaire conçue dans Outlook  
 Quand vous concevez une zone de formulaire dans Outlook, vous pouvez lui ajouter des contrôles Outlook natifs.  Les contrôles Outlook natifs vous permettent de créer une liaison avec les données Outlook au moment du design.  Toutefois, vous ne pouvez pas utiliser ensuite le Concepteur de zones de formulaire pour ajouter des contrôles managés ou modifier la conception de la zone de formulaire.  
  
 Vous pouvez importer des zones de formulaire dans un projet de complément VSTO Outlook à l'aide de l'Assistant **Nouvelle zone de formulaire Outlook**.  Dans la page **Sélectionnez la méthode de création de la zone de formulaire**, sélectionnez **Importer un fichier de stockage de formulaire Outlook \(.ofs\)**.  Vous pouvez ensuite accéder à l'emplacement d'un fichier de stockage de formulaire Outlook \(.ofs\).  \(Outlook enregistre les zones de formulaire en tant que fichiers .ofs.\)  
  
 L'Assistant **Nouvelle zone de formulaire Outlook** copie le fichier .ofs dans le répertoire du projet et ajoute des références de contrôle au fichier du Concepteur de zone de formulaire.  Vous pouvez ensuite gérer les événements de contrôle dans le fichier de code de région de formulaire.  
  
 Pour gérer des événements dans un projet Visual Basic, sélectionnez un événement dans la liste des noms de méthodes en haut de l'éditeur de code.  
  
 Pour gérer des événements dans un projet C\#, abonnez\-vous aux événements de contrôle dans la méthode <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>.  Pour plus d'informations, consultez [Comment : s'abonner et annuler l'abonnement à des événements &#40;Guide de programmation C&#35;&#41;](../Topic/How%20to:%20Subscribe%20to%20and%20Unsubscribe%20from%20Events%20(C%23%20Programming%20Guide).md).  
  
 Vous pouvez modifier les propriétés des zones de formulaire dans la méthode `InitializeManifest` de la classe de fabrique de zones de formulaire.  
  
> [!NOTE]  
>  Pour importer une zone de formulaire, vous devez travailler dans un projet qui cible la version d'Outlook que vous avez installée sur l'ordinateur de développement.  Par exemple, si Outlook 2010 est installé, l'importation d'une zone de formulaire fonctionne uniquement dans un projet créé à l'aide du modèle de projet **Complément Outlook 2010**.  
  
### Mise à jour de la conception d'une zone de formulaire importée  
 Vous pouvez ajouter, supprimer ou modifier des contrôles dans la zone de formulaire.  Avant cela, sauvegardez tout le code que vous avez ajouté au fichier de code de la zone de formulaire.  Ensuite, ouvrez le fichier .ofs dans Outlook, modifiez la zone de formulaire, puis enregistrez les modifications.  Utilisez l'Assistant **Nouvelle zone de formulaire Outlook** pour importer le fichier .ofs modifié.  Vous pouvez ensuite coller votre code dans le fichier de code de la nouvelle zone de formulaire.  
  
##  <a name="AddingCustomCode"></a> Ajout d'un code personnalisé à une zone de formulaire  
 L'espace de noms <xref:Microsoft.Office.Tools.Outlook> vous donne accès aux classes qui représentent la zone de formulaire, à l'élément Outlook qui affiche la zone de formulaire et à d'autres éléments utiles.  L'élément **Zone de formulaire Outlook** ajoute automatiquement une référence à cet assembly dans le projet et insère l'instruction **using** ou **Imports** appropriée au début du fichier de code de la zone de formulaire.  
  
 Vous pouvez utiliser des classes, des méthodes et des propriétés dans l'espace de noms Microsoft.Office.Interop.Outlook pour accomplir la plupart de vos tâches de programmation Outlook.  Pour plus d'informations sur le modèle d'objet Outlook, consultez [Vue d'ensemble du modèle d'objet Outlook](../vsto/outlook-object-model-overview.md).  Pour obtenir des exemples de tâches standard utilisant le modèle d'objet Outlook, consultez [Solutions Outlook](../vsto/outlook-solutions.md).  
  
###  <a name="HandlingFormRegionEvents"></a> Gestion des événements de zone de formulaire  
 L'élément **Zone de formulaire Outlook** ajoute automatiquement les trois gestionnaires d'événements suivants au fichier de code de la zone de formulaire.  
  
|Événement|Description|  
|---------------|-----------------|  
|FormRegionInitializing|Se produit avant l'initialisation de la zone de formulaire.  Vous pouvez vérifier des conditions dans ce gestionnaire d'événements pour déterminer si Outlook doit afficher la zone de formulaire.  Pour plus d'informations, consultez [Comment : empêcher Outlook d'afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|  
|FormRegionShowing|Se produit après la création d'une instance de la zone de formulaire, mais avant l'affichage de la zone de formulaire.|  
|FormRegionClosed|Se produit avant la fermeture de la zone de formulaire.|  
  
##  <a name="Building"></a> Génération du projet  
 Quand vous générez un projet de complément VSTO Outlook qui contient une zone de formulaire, Visual Studio ajoute les informations suivantes dans le Registre :  
  
-   une clé pour chaque classe de message associée à une ou plusieurs zones de formulaire,  
  
-   une entrée pour chaque zone de formulaire et une valeur associée représentant le nom du complément VSTO Outlook.  
  
 Outlook utilise ces informations pour charger les zones de formulaire.  
  
##  <a name="Debugging"></a> Débogage d'une zone de formulaire  
 Pour déboguer un complément VSTO Outlook contenant une zone de formulaire, procédez comme pour tout autre projet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Quand vous démarrez le débogueur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Visual Studio démarre automatiquement Outlook.  
  
 Pour afficher la zone de formulaire, vous devez ouvrir l'élément Outlook approprié.  Par exemple, si une zone de formulaire adjacente est ajoutée au bas d'un élément de messagerie, ouvrez un élément de messagerie.  
  
##  <a name="Deploying"></a> Déploiement d'une zone de formulaire  
 Les zones de formulaire sont déployées automatiquement avec le complément VSTO Outlook associé.  Il est donc inutile d'exécuter des tâches spéciales pour déployer une zone de formulaire.  Pour plus d'informations sur le déploiement de compléments VSTO, consultez [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Directives pour la création de zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Fournit des informations pouvant vous aider à optimiser vos zones de formulaire et à éviter d'éventuels problèmes.|  
|[Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Montre comment créer une zone de formulaire pour étendre un formulaire Microsoft Office Outlook standard ou personnalisé à l'aide de l'Assistant **Nouvelle zone de formulaire Outlook**.|  
|[Association d'une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Explique comment spécifier les éléments Microsoft Office Outlook qui doivent afficher une zone de formulaire en associant cette dernière à la classe de message de chaque élément.|  
|[Procédure pas à pas : conception d'une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)|Montre comment concevoir une zone de formulaire personnalisée qui apparaît en tant que nouvelle page dans la fenêtre Inspecteur d'un élément de contact.|  
|[Procédure pas à pas : importation d'une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Montre comment concevoir une zone de formulaire dans Microsoft Office Outlook, puis importer la zone de formulaire dans un projet de complément VSTO Outlook à l'aide de l'Assistant **Nouvelle zone de formulaire Outlook**.|  
|[Accès à une zone de formulaire au moment de l'exécution](../vsto/accessing-a-form-region-at-run-time.md)|Explique comment écrire du code pour afficher, masquer ou modifier des contrôles dans une zone de formulaire, et comment permettre aux utilisateurs d'exécuter le code à partir d'autres zones de votre projet à l'aide de la classe `Globals`.|  
|[Comment : empêcher Outlook d'afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Montre comment empêcher Microsoft Office Outlook d'afficher une zone de formulaire pour un élément particulier.|  
|Montre comment accéder à l'élément Outlook dans lequel une zone de formulaire apparaît.|  
|[Actions personnalisées dans les zones de formulaire Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|Explique comment permettre aux utilisateurs de répondre à un élément Outlook.|  
  
  