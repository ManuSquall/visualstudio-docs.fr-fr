---
title: "Proc&#233;dure pas &#224; pas&#160;: d&#233;ploiement d&#39;une d&#233;finition de liste de t&#226;ches de projet"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, déployer"
ms.assetid: 18b62016-ed30-4dd1-9dfc-0d7e82c6767f
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Proc&#233;dure pas &#224; pas&#160;: d&#233;ploiement d&#39;une d&#233;finition de liste de t&#226;ches de projet
  Cette explication montre comment créer, personnaliser, déboguer et déployer une liste SharePoint à l'aide de [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] en vue d'effectuer le suivi des tâches du projet.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   [Création d'une liste SharePoint](#CreatingListDef).  
  
-   [Création d'une liste SharePoint](#CreatingListDef).  
  
-   [Ajout d'un récepteur d'événements](#AddEventRcvr).  
  
-   [Personnalisation de la fonctionnalité Liste des tâches d'un projet](#CustomizeFeature).  
  
-   [Génération et test de la liste des tâches d'un projet](#BuildTest).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de Microsoft Windows et SharePoint prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] ou une édition de Visual Studio Application Lifecycle Management \(ALM\).  
  
##  <a name="CreatingListDef"></a> Création d'une liste SharePoint  
 Créez un projet de liste SharePoint et associez la définition de liste aux tâches.  
  
#### Pour créer un projet de de liste SharePoint  
  
1.  Ouvrez la boîte de dialogue **Nouveau projet**, développez le nœud **SharePoint**, puis choisissez le noeud **2010**.  
  
2.  Dans le volet **Modèles**, choisissez le **Projet SharePoint 2010** , remplacez le nom du projet par ProjectTaskList, puis cliquez sur **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
3.  Spécifiez le site local SharePoint que vous utilisez pour déboguer, sélectionnez la case d'option **Déployer en tant que solution de batterie**, puis cliquez sur le bouton **Terminer**.  
  
4.  Ouvrez le menu contextuel de ce projet, puis choisissez **Ajouter**, **Nouvel Elément**.  
  
5.  Dans le volet **Modèles**, choisissez le modèle**Liste**, puis le bouton **Ajouter**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
6.  Dans la zone **Quel nom voulez\-vous afficher pour votre liste ?**, entrez la liste des tâches du projet.  
  
7.  Sélectionnez la case d'option **Créez une liste non personnalisable à partir d'un type existant de**, puis, dans la liste, choisissez **Tâches**, puis cliquez sur le bouton **Terminer**.  
  
     La liste, le composant, et le package s'affichent dans **Explorateur de solutions**.  
  
##  <a name="AddEventRcvr"></a> Ajout d'un récepteur d'événements  
 Dans la liste de tâches, vous pouvez ajouter un récepteur d'événements permettant de déterminer automatiquement la date d'échéance et la description de la tâche.  La procédure suivante ajoute un simple gestionnaire d'événements à l'instance de liste comme récepteur d'événements.  
  
#### Pour ajouter un récepteur d'événements  
  
1.  Ouvrez le menu contextuel pour le nœud du projet, sélectionnez **Ajouter**, puis **Nouvel élément**.  
  
2.  Dans la liste de modèles SharePoint 2010, choisissez le modèle **Récepteur d'événements** et ensuite appelez\-le **RécepteurÉvénementsListeTâchesProjet**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
3.  Dans la page **Choisir les paramètres de récepteur d'événements**, choisissez **Liste des événements d'élément** comme récepteur d'événements dans la liste **Le type de récepteur d'événements que vous souhaitez**.  
  
4.  Dans la liste **Quel élément doit être la source d'événement**, choisissez **Tâches**.  
  
5.  Dans la liste des événements à gérer, sélectionner la case à cocher en face de l'option **Un élément a été ajouté**, puis cliquez sur le bouton **Terminer**.  
  
     Un nouveau nœud de récepteur d'événements est ajouté au projet avec un fichier de code nommé **RécepteurÉvénementsListeTâchesProjet**.  
  
6.  Ajoutez le code à la méthode `ItemAdded` dans le fichier de code **RécepteurÉvénementsListeTâchesProjet**.  Une date d'échéance et une description par défaut sont associées à chaque nouvelle tâche ajoutée.  La date d'échéance par défaut est le 1er juillet 2009.  
  
     [!code-csharp[SPProjectTaskList#1](../snippets/csharp/VS_Snippets_OfficeSP/spprojecttasklist/cs/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]
     [!code-vb[SPProjectTaskList#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spprojecttasklist/vb/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]  
  
##  <a name="CustomizeFeature"></a> Personnalisation de la fonctionnalité Liste des tâches d'un projet  
 Lorsque vous créez une solution SharePoint, Visual Studio crée automatiquement des fonctionnalités pour les éléments de projet par défaut.  Vous pouvez personnaliser les paramètres de liste des tâches du projet pour le site SharePoint à l'aide du Concepteur de fonctionnalités.  
  
#### Pour personnaliser la fonctionnalité Liste des tâches d'un projet  
  
1.  Dans l'**Explorateur de solutions**, développez **Fonctionnalités**.  
  
2.  Ouvrez le menu contextuel de **Composant1**, puis choisissez **Designer d'affichage**.  
  
3.  Dans la zone **Titre**, tapez **Composant de liste des tâches d'un projet**.  
  
4.  Dans la liste **Portée**, choisissez **Web**.  
  
5.  Dans la fenêtre **Propriétés**, entrez **1.0.0.0** comme valeur pour la propriété **Version**.  
  
##  <a name="CustomizePackage"></a> Personnalisation du package Liste des tâches d'un projet  
 Lorsque vous créez un projet SharePoint, Visual Studio ajoute automatiquement les fonctionnalités contenant les éléments de projet par défaut au package.  Il est possible de personnaliser les paramètres de liste des tâches du projet pour le site SharePoint à l'aide du Concepteur de packages.  
  
#### Pour personnaliser le package Liste des tâches d'un projet  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel de **Package**, puis choisissez **Concepteur de vue**.  
  
2.  Dans la zone **Nom**, tapez **ProjectTaskListPackage.aspx**.  
  
3.  Activez la case à cocher **remettre à zéro le serveur de rapports**.  
  
##  <a name="BuildTest"></a> Génération et test de la liste des tâches d'un projet  
 Lorsque vous exécutez le projet, le site SharePoint s'ouvre.  Vous devez, toutefois, accéder manuellement à l'emplacement de la liste des tâches.  
  
#### Pour tester la liste des tâches d'un projet  
  
1.  Choisissez la clé F5 pour générer et déployer votre liste des tâches du projet.  
  
     Le site SharePoint s'ouvre.  
  
2.  Sélectionnez l'onglet **Accueil**.  
  
3.  Dans les crochets gauche, cliquez sur le lien **Liste des tâches du projet**.  
  
     Cela a pour effet d'afficher la page Liste des tâches d'un projet.  
  
4.  Dans l'onglet **Répertorier les outils**, choisissez l'onglet **Éléments**.  
  
5.  Dans le groupe **Éléments**, cliquez sur le bouton **Nouvel élément**.  
  
6.  Dans la zone de texte **Titre**, entrez Tâche1.  
  
7.  Cliquez sur le bouton **Enregistrer**.  
  
     Après avoir actualisé le site, la tâche intitulée **Tâche1** apparaît avec une date d'échéance correspondant au 7\/1\/2009.  
  
8.  Sélectionner **Tâche1**.  
  
     La vue détaillée de la tâche apparaît et la description indique qu'il s'agit d'une tâche critique.  
  
##  <a name="Deploy"></a> Déploiement de la liste des tâches d'un projet  
 Après avoir généré et testé la liste des tâches d'un projet, vous pouvez le déployer sur le *système local* ou un *système distant*.  Le système local est le même ordinateur sur lequel vous avez développé la solution, alors qu'un système distant est un autre ordinateur.  
  
#### Pour déployer la liste des tâches d'un projet sur le système local  
  
1.  Dans la barre de menus Visual Studio, choisissez **Générer**, **Déployer la solution**.  
  
     Visual Studio recycle le pool d'applications IIS, retire toute version existante de la solution, copie le fichier de package de solution \(.wsp\) dans SharePoint, puis active ses fonctionnalités.  Vous pouvez maintenant utiliser la solution dans SharePoint.  Pour plus d'informations sur les étapes de la configuration du déploiement, consultez [Comment : modifier une configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
#### Pour déployer la liste des tâches d'un projet sur un système distant  
  
1.  Dans la barre de menus Visual Studio, choisissez **Générer**, **Publier**.  
  
2.  Dans la boîte de dialogue **Publier**, sélectionnez la case d'option **Publier dans le système de fichiers**.  
  
     Vous pouvez modifier l'emplacement cible dans la boîte de dialogue **Publier** en choisissant le bouton ![Icône du bouton de sélection (...)](~/sharepoint/media/ellipsisicon.gif "Icône du bouton de sélection (...)") puis en accédant à un autre emplacement.  
  
3.  Cliquez sur le bouton **Publish**  
  
     Un fichier .wsp est créé pour la solution.  
  
4.  Copiez le fichier .wsp sur le système distant SharePoint.  
  
5.  Utilisez la commande `Add-SPUserSolution` PowerShell pour installer le package sur l'installation SharePoint distante. \(Pour les solutions de batterie, utilisez la commande `Add-SPSolution`.\)  
  
     Par exemple, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.  
  
6.  Utilisez la commande `Install-SPUserSolution` PowerShell pour déployer la solution. \(Pour les solutions de batterie, utilisez la commande `Install-SPSolution`.\)  
  
     Par exemple, `Install-SPUserSolution –Identity ProjectTaskList.wsp –Site http://NewSiteName`.  
  
     Pour plus d'informations sur le déploiement distant, consultez [Utilisation des solutions](http://go.microsoft.com/fwlink/?LinkId=217680) et [Ajout et déploiement de solutions avec PowerShell dans SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).  
  
## Étapes suivantes  
 Pour en savoir plus au sujet du mode de personnalisation et de déploiement des solutions SharePoint, reportez\-vous aux rubriques suivantes :  
  
-   [Procédure pas à pas : création d'une colonne de site, d'un type de contenu et d'une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [Comment : créer un récepteur d'événements](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [Windows PowerShell pour SharePoint server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  