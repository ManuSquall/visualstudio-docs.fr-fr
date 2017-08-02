---
title: "Cr&#233;ation de solutions de flux de travail SharePoint"
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
  - "VSTO.NewSharePointWorkflowWizard.Page3"
  - "VS.SharePointTools.Workflow.WorkflowName"
  - "VSTO.NewSharePointWorkflowWizard.Page2"
  - "VSTO.NewSharePointWorkflowWizard.Page1"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, workflows"
  - "workflows (développement SharePoint dans Visual Studio)"
ms.assetid: fe79b99a-cb7c-4a14-8d9f-bce0c0805ba0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Cr&#233;ation de solutions de flux de travail SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] offre les outils dont vous avez besoin pour créer des modèles de flux de travail personnalisés qui gèrent le cycle de vie des documents et des éléments de liste dans un site Web SharePoint.  Les éléments fournis incluent un concepteur, un jeu de contrôles d'activité et les références d'assembly nécessaires.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclut également l'**Assistant Personnalisation de SharePoint** pour faciliter la création et la configuration des flux de travail.  
  
 Pour connaître les conditions préalables à la création de projets SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  Pour plus d'informations sur SharePoint, consultez[Produits et technologies Microsoft SharePoint](http://go.microsoft.com/fwlink/?LinkId=178470).  
  
## Flux de travail SharePoint  
 Lorsque vous ajoutez un flux de travail à une bibliothèque ou une liste SharePoint, vous appliquez un processus métier sur tous les éléments de la bibliothèque ou de la liste.  Un flux de travail décrit les actions que le système ou les utilisateurs doivent exécuter sur chaque élément, telles que l'envoi de l'élément à modifier puis à réviser.  Ces actions, appelées *activités*, sont les blocs de construction du flux de travail.  
  
 Vous pouvez créer des flux de travail SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et les déployer sur un site Web SharePoint.  Après avoir déployé un flux de travail sur SharePoint, il convient de l'associer à une bibliothèque ou à une liste.  Il peut ensuite être démarré automatiquement via un processus ou manuellement par un utilisateur.  Pour plus d'informations sur le fonctionnement de flux de travail, consultez [Utilisation de flux de travail pour gérer les processus](http://go.microsoft.com/fwlink/?LinkId=79757).  
  
## Création de flux de travail SharePoint personnalisés  
 Deux projets de flux de travail SharePoint sont disponibles dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] : **Flux de travail séquentiel** et **Flux de travail de machine à états**.  
  
 Un *flux de travail séquentiel* représente une série d'étapes  effectuées à tour de rôle jusqu'à la dernière activité.  Ces flux de travail sont toujours exécutés dans un ordre séquentiel.  Étant donné qu'ils peuvent recevoir des événements externes et qu'ils obéissent à des flux logiques parallèles, l'ordre exact d'exécution peut varier.  L'illustration suivante montre un exemple d'un flux de travail séquentiel.  
  
 ![Flux de travail séquentiel](../sharepoint/media/sp-sequential.png "Flux de travail séquentiel")  
  
 Un *flux de travail de machine à états* représente un jeu d'états, de transitions et d'actions.  Les étapes dans un flux de travail de machine à états sont réalisées de façon asynchrone.  Cela signifie qu'elles ne sont pas nécessairement exécutées l'une après l'autre, mais qu'elles sont déclenchées par des actions et des états.  Un état correspond à l'état de démarrage, lequel est suivi d'une transition vers un autre état en fonction d'un événement.  La machine à états peut être associée à un dernier état qui détermine la fin du flux de travail.  Le diagramme suivant affiche un exemple d'un flux de travail de machine à états.  
  
 ![Workflow de l'ordinateur d'état](../sharepoint/media/sp-state.png "Workflow de l'ordinateur d'état")  
  
 Pour plus d'informations sur les types de flux de travail, consultez [Types de flux de travail](http://go.microsoft.com/fwlink/?LinkId=178995).  
  
### Utilisation de l'Assistant  
 Lorsque vous créez un projet de flux de travail SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il faut d'abord définir ses paramètres dans l'**Assistant Personnalisation de SharePoint**.  L'Assistant se fonde sur ces paramètres pour créer un projet dans l'**Explorateur de solutions**.  Ce projet contient un fichier de code, plusieurs fichiers utilisés pour déployer le modèle de flux de travail et des références aux assemblys dont vous avez besoin pour définir un modèle de flux de travail SharePoint personnalisé.  
  
 Après avoir mis en place le flux de travail, vous êtes libre de modifier ses propriétés dans la fenêtre Propriétés.  Bien que la plupart des propriétés de flux de travail soient modifiables directement dans la fenêtre Propriétés, certaines d'entre elles exigent que vous cliquiez sur un bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](~/sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")\) pour modifier leurs valeurs.  Ce bouton a pour effet de redémarrer l'**Assistant Personnalisation de SharePoint**.  Après avoir changé les valeurs des propriétés, cliquez sur le bouton **Terminer** pour les valider.  
  
> [!NOTE]  
>  La propriété **Type de flux de travail** est une propriété en lecture seule non modifiable.  Pour modifier le type de flux de travail, la seule solution est de créer un autre flux de travail.  
  
## Conception d'un flux de travail SharePoint  
 Après avoir défini toutes les étapes du processus métier, servez\-vous du Concepteur de flux de travail [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour mettre au point le flux de travail SharePoint.  Pour ouvrir le concepteur, double\-cliquez sur Workflow1.cs ou Workflow1.vb dans **Explorateur de solutions**, ou ouvrez le menu contextuel de l'un ou l'autre de ces fichiers puis choisissez **Ouvrir**.  
  
### Activités  
 Pour concevoir un flux de travail, ajoutez des activités de la **Boîte à outils** à une *planification de flux de travail* du concepteur.  Une planification de flux de travail contient la séquence d'activités dans l'ordre dans lequel elle doit s'exécuter.  
  
 Il existe deux types d'activités :  
  
-   Les *activités simples* exécutent une seule unité de travail, telle que "délai d'1 jour" ou "démarrage du service Web".  
  
-   Les *activités composites* contiennent d'autres activités ; par exemple, une activité conditionnelle peut contenir deux branches.  
  
 Les deux types d'activités sont disponibles dans la **Boîte à outils**.  
  
 Les activités peuvent avoir des propriétés, des méthodes et des événements.  Utilisez la fenêtre **Propriétés** pour définir les propriétés d'une activité.  
  
 Vous pouvez également créer une activité personnalisée.  Pour plus d'informations, consultez [Procédures pas à pas : création d'une activité de workflow de site personnalisée](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).  
  
 Les activités sont réparties dans les deux onglets suivants de la **Boîte à outils** :  
  
-   **Flux de travail SharePoint**  
  
-   **Windows Workflow v3.0**  
  
-   **Windows Workflow v3.5**  
  
 Toutes les activités de flux de travail de base ne sont pas prises en charge par SharePoint.  Pour plus d'informations, consultez [Opérations de flux de travail pour une présentation de Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### Activités du flux de travail SharePoint  
 Les onglets **Flux de travail SharePoint** contiennent des activités spécialisées qui sont conçues pour [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)].  Ces activités ont pour but de simplifier et de rationaliser le développement des flux de travail des cycles de vie des documents.  Pour plus d'informations sur les activités répertoriées dans l'onglet **Flux de travail SharePoint**, consultez [Vue d'ensemble des activités de flux de travail pour Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### Activités Windows Workflow  
 Les onglets **Windows Workflow** contiennent les activités fournies par le [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)].  Vous pouvez utiliser ces activités pour créer des planifications de flux de travail pour tout type d'application Windows Workflow.  
  
 Pour plus d'informations sur les activités répertoriées dans les onglets **Windows Workflow**, consultez [Activités Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=156096).  Pour plus d'informations sur Windows Workflow Foundation, consultez [Vue d'ensemble de Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=128632).  
  
### Utilisation d'activités dans le concepteur  
 Votre planification de flux de travail peut contenir une combinaison d'activités Windows Workflow et d'activités de flux de travail SharePoint.  
  
 Le concepteur affiche des signaux visuels pour vous aider à positionner et configurer correctement des activités.  Lorsque vous faites glisser ou copiez une activité sur la planification de flux de travail, le concepteur affiche des icônes contenant le signe plus \(\+\) vert qui vous indiquent des emplacements valides pour cette activité dans le flux de travail.  Vous ne pouvez pas positionner d'activité à un emplacement où elle ne serait pas valide.  Par exemple, vous ne pouvez pas positionner d'activité d'envoi comme première activité dans une branche d'activité d'écoute.  Pour plus d'informations, consultez le [Centre de développement du Concepteur SharePoint](http://go.microsoft.com/fwlink/?LinkId=178476).  
  
## Collecte d'informations pendant le flux de travail  
 Vous pouvez souhaiter rassembler des informations d'utilisateurs à des moments prédéfinis dans le flux de travail.  Vous pouvez rassembler des informations à l'aide de formulaires ou de propriétés d'élément.  
  
### Formulaires  
 Les formulaires sont semblables aux boîtes de dialogue qui contiennent des questions et offrent aux utilisateurs des moyens de fournir des réponses.  
  
 Il existe quatre types de formulaires utilisables dans un flux de travail :  
  
-   Association  
  
-   Initiation  
  
-   Modification  
  
-   Tâche  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] offre, en outre, des modèles d'élément pour les formulaires Association et Initiation.  Un administrateur chargé de la mise en place d'un flux de travail pourrait utiliser un *formulaire Association* pour entrer les paramètres appropriés \(seuil maximum de dépense d'un flux de travail de frais, par exemple\).  Un *formulaire de lancement* est un formulaire qui permet à l'utilisateur d'un flux de travail d'écrire la quantité qu'ils ont dépensée dans le flux de travail.  Pour plus d'informations sur ces types de formes, consultez [Modèles de projets et d'éléments de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
### Propriétés de l'élément  
 Vous pouvez également rassembler des informations auprès d'utilisateurs en utilisant les propriétés d'un élément de la bibliothèque ou de la liste SharePoint.  Le fichier de code principal \(Workflow1.cs ou Workflow1.vb\) déclare une instance de la classe Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties nommée `workflowProperties`.  Utilisez l'objet `workflowProperties` pour accéder aux propriétés de la bibliothèque ou de la liste dans le code.  Pour obtenir un exemple, consultez [Procédure pas à pas : création et débogage d'une solution de flux de travail SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).  
  
## Débogage d'un modèle de flux de travail SharePoint  
 Vous pouvez déboguer un projet de flux de travail SharePoint comme vous le feriez pour d'autres projets [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] de type Web.  Lorsque vous démarrez le débogueur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise les paramètres spécifiés dans l'**Assistant Personnalisation de SharePoint** pour ouvrir le site Web SharePoint approprié et associer automatiquement le modèle de flux de travail à la bibliothèque ou à la liste qui convient.  En outre, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] joint le débogueur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] au processus [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] nommé w3wp.exe.  
  
 Pour tester le flux de travail, vous devez le démarrer manuellement.  Pour plus d'informations, consultez la section « Débogage de flux de travail » dans [Débogage de solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  Pour plus d'informations sur le débogage de l'application Web [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], consultez [Débogage d'applications et de scripts Web](../debugger/debugging-web-applications-and-script.md).  
  
## Déploiement d'un modèle de flux de travail SharePoint  
 Les projets de flux de travail SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sont déployés de la même manière que les autres projets SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Pour plus d'informations, consultez [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).  
  
## Importation de flux de travail globalement réutilisables  
 SharePoint Designer permet de créer non seulement des flux de travail réutilisables qui sont spécifiques au site, mais également des *flux de travail globalement réutilisables* qui peuvent être employés par tout site SharePoint.  Le projet Importer le flux de travail réutilisable de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne permet pas d'importer des flux de travail globalement réutilisables.  Toutefois, vous pouvez soit utiliser SharePoint Designer pour convertir un flux de travail globalement réutilisable en flux de travail réutilisable soit importer le flux de travail en tant que flux de travail déclaratif non converti.  Pour plus d'informations, consultez [Importation d'éléments d'un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Procédure pas à pas : création et débogage d'une solution de flux de travail SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Explique comment procéder, étape par étape, pour créer et déboguer un flux de travail [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] simple.|  
|[Procédure pas à pas : création d'un flux de travail avec des formulaires d'association et d'initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Explique comment procéder, étape par étape, pour créer un flux de travail [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] plus complet avec des formulaires Association et Initiation.|  
|[Procédure pas à pas : ajout d'une page d'application à un flux de travail](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Explique comment ajouter une page d'application .aspx supplémentaire faisant un bilan des données entrées dans le flux de travail dont il est question à la rubrique [Procédure pas à pas : création d'un flux de travail avec des formulaires d'association et d'initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|  
|[Procédures pas à pas : création d'une activité de workflow de site personnalisée](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Montre comment effectuer les deux tâches essentielles que sont la création d'un flux de travail au niveau du site et la création d'une activité de flux de travail personnalisée.|  
|[Procédure pas à pas : importation d'un flux de travail réutilisable de SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Montre comment importer des flux de travail déclaratifs réutilisables créés avec SharePoint Designer 2010 dans un projet SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
  
## Voir aussi  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)  
  
  