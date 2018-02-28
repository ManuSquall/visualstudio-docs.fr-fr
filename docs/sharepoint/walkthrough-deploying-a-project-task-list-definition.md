---
title: "Procédure pas à pas : Déploiement d’une définition de liste de tâches de projet | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 4d91b1b40ac99ca3984f772b77a16258a1bddf51
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-deploying-a-project-task-list-definition"></a>Procédure pas à pas : déploiement d’une définition de liste de tâches de projet
  Cette procédure pas à pas explique comment créer, personnaliser, déboguer et déployer une liste SharePoint à l'aide de [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] en vue d'effectuer le suivi des tâches du projet.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   [Création d’une liste SharePoint](#CreatingListDef).  
  
-   [Création d’une liste SharePoint](#CreatingListDef).  
  
-   [Ajout d’un récepteur d’événements](#AddEventRcvr).  
  
-   [Personnalisation de la fonctionnalité de liste des tâches de projet](#CustomizeFeature).  
  
-   [Liste des tâches de génération et test du projet](#BuildTest).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Microsoft Windows et SharePoint. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)]ou une édition de Visual Studio Application Lifecycle Management (ALM).  
  
##  <a name="CreatingListDef"></a>Création d’une liste SharePoint  
 Créez un projet de liste SharePoint et associez la définition de liste aux tâches.  
  
#### <a name="to-create-a-sharepoint-list-project"></a>Pour créer un projet de liste SharePoint  
  
1.  Ouvrir le **nouveau projet** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
2.  Dans le **modèles** volet, choisissez la **projet SharePoint 2010** modèle, nommez le projet **ProjectTaskList**, puis choisissez le **OK**bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
3.  Spécifiez le site SharePoint local que vous utilisez pour le débogage, choisissez le **déployer une solution de batterie de serveurs** case d’option, puis choisissez le **Terminer** bouton.  
  
4.  Ouvrez le menu contextuel du projet, puis choisissez **ajouter**, **un nouvel élément**.  
  
5.  Dans le **modèles** volet, choisissez la **liste** modèle, puis choisissez le **ajouter** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
6.  Dans le **quel nom voulez-vous afficher pour votre liste ?** , entrez **liste des tâches de projet**.  
  
7.  Choisissez le **créer une liste non personnalisable basée sur un type de liste existant** case d’option, puis, dans la liste, choisissez **tâches**, puis choisissez le **Terminer** bouton.  
  
     La liste, la fonctionnalité et le package s’affichent dans **l’Explorateur de solutions**.  
  
##  <a name="AddEventRcvr"></a>Ajout d’un récepteur d’événements  
 Dans la liste de tâches, vous pouvez ajouter un récepteur d’événements permettant de déterminer automatiquement la date d’échéance et la description de la tâche. La procédure suivante ajoute un gestionnaire d’événements simple à l’instance de liste comme un récepteur d’événements.  
  
#### <a name="to-add-an-event-receiver"></a>Pour ajouter un récepteur d’événements  
  
1.  Ouvrez le menu contextuel du nœud de projet, choisissez **ajouter**, puis choisissez **un nouvel élément**.  
  
2.  Dans la liste de modèles SharePoint, choisissez le **récepteur d’événements** modèle, puis nommez-le **ProjectTaskListEventReceiver**.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
3.  Sur le **choisir les paramètres de récepteur d’événements** page, choisissez **événements d’élément de liste** comme type de récepteur d’événements dans le **le type de récepteur d’événements voulez-vous** liste.  
  
4.  Dans le **quel élément doit être la source d’événements** , choisissez **tâches**.  
  
5.  Dans la liste des événements à gérer, sélectionnez la case à cocher à côté **un élément a été ajouté**, puis choisissez le **Terminer** bouton.  
  
     Un nouveau nœud de récepteur d’événements est ajouté au projet avec un fichier de code nommé **ProjectTaskListEventReceiver**.  
  
6.  Ajoutez le code pour le `ItemAdded` méthode dans le **ProjectTaskListEventReceiver** fichier de code. Chaque fois qu’une nouvelle tâche est ajoutée, date d’échéance et une description par défaut est ajouté à la tâche. La valeur par défaut due date est le 1er juillet 2009.  
  
     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]  
  
##  <a name="CustomizeFeature"></a>Personnalisation de la fonctionnalité de liste des tâches de projet  
 Lorsque vous créez une solution SharePoint, Visual Studio crée automatiquement les fonctionnalités pour la valeur par défaut des éléments de projet. Vous pouvez personnaliser les paramètres de liste des tâches de projet pour le site SharePoint à l’aide du Concepteur de fonctionnalités.  
  
#### <a name="to-customize-the-project-task-list-feature"></a>Pour personnaliser la fonctionnalité de liste des tâches de projet  
  
1.  Dans **l’Explorateur de solutions**, développez **fonctionnalités**.  
  
2.  Ouvrez le menu contextuel pour **Feature1**, puis choisissez **Concepteur de vue**.  
  
3.  Dans le **titre** , entrez **fonctionnalité liste des tâches projet**.  
  
4.  Dans le **étendue** , choisissez **Web**.  
  
5.  Dans le **propriétés** fenêtre, entrez **1.0.0.0** comme valeur pour le **Version** propriété.  
  
##  <a name="CustomizePackage"></a>Personnalisation du Package de liste des tâches de projet  
 Lorsque vous créez un projet SharePoint, Visual Studio ajoute automatiquement les fonctionnalités qui contiennent les éléments de projet par défaut pour le package. Vous pouvez personnaliser les paramètres de liste des tâches de projet pour le site SharePoint à l’aide du Concepteur de packages.  
  
#### <a name="to-customize-the-project-task-list-package"></a>Pour personnaliser le package de liste des tâches de projet  
  
1.  Dans **SolutionExplorer**, ouvrez le menu contextuel pour **Package**, puis choisissez **Concepteur de vue**.  
  
2.  Dans le **nom** , entrez **ProjectTaskListPackage**.  
  
3.  Sélectionnez le **réinitialiser le serveur Web** case à cocher.  
  
##  <a name="BuildTest"></a>Génération et test de la liste de tâches de projet  
 Lorsque vous exécutez le projet, le site SharePoint s’ouvre. Toutefois, vous devez accéder manuellement à l’emplacement de la liste des tâches.  
  
#### <a name="to-test-the-project-task-list"></a>Pour tester la liste de tâches de projet  
  
1.  Sélectionnez la touche F5 pour générer et déployer votre liste des tâches du projet.  
  
     Le site SharePoint s’ouvre.  
  
2.  Choisissez le **accueil** onglet.  
  
3.  Dans la barre latérale gauche, choisissez le **liste des tâches de projet** lien.  
  
     La page de liste des tâches de projet s’affiche.  
  
4.  Dans le **outils de liste** , choisir le **éléments** onglet.  
  
5.  Dans le **éléments** groupe, choisissez le **un nouvel élément** bouton.  
  
6.  Dans le **titre** texte, entrez **Task1**.  
  
7.  Choisissez le **enregistrer** bouton.  
  
     Une fois que le site est actualisé, le **Task1** tâche apparaît avec une date d’échéance de 7/1/2009.  
  
8.  Choisissez **Task1**.  
  
     La vue détaillée de la tâche apparaît et la description indique « Il s’agit d’une tâche critique. »  
  
##  <a name="Deploy"></a>Déploiement de la liste de tâches de projet  
 Une fois que vous générez et testez la liste de tâches du projet, vous pouvez le déployer à la *système local* ou un *système distant*. Le système local est le même ordinateur que celui sur lequel vous avez développé la solution, tandis qu’un système distant est un autre ordinateur.  
  
#### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Pour déployer la liste des tâches projet sur le système local  
  
1.  Dans la barre de menus de Visual Studio, choisissez **générer**, **déployer la Solution**.  
  
     Visual Studio recycle le pool d’applications IIS, retire toutes les versions existantes de la solution, copie le fichier de package (.wsp) de solution SharePoint, puis active ses fonctionnalités. Vous pouvez maintenant utiliser la solution dans SharePoint. Pour plus d’informations sur les étapes de configuration de déploiement, consultez [Comment : modifier une Configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
#### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Pour déployer la liste des tâches projet vers un système distant  
  
1.  Dans la barre de menus de Visual Studio, choisissez **générer**, **publier**.  
  
2.  Dans le **publier** boîte de dialogue, choisissez le **publier sur le système de fichiers** case d’option.  
  
     Vous pouvez modifier l’emplacement cible dans le **publier** boîte de dialogue en cliquant sur le bouton de sélection ![icône des points de suspension](../sharepoint/media/ellipsisicon.gif "icône des points de suspension") et puis navigué vers un autre emplacement.  
  
3.  Choisissez le **publier** bouton.  
  
     Un fichier .wsp est créé pour la solution.  
  
4.  Copiez le fichier .wsp sur le système de SharePoint à distance.  
  
5.  Utilisez le PowerShell `Add-SPUserSolution` commande pour installer le package sur l’installation de SharePoint à distance. (Pour les solutions de batterie de serveurs, utilisez la `Add-SPSolution` commande.)  
  
     Par exemple, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.  
  
6.  Utilisez le PowerShell `Install-SPUserSolution` commande pour déployer la solution. (Pour les solutions de batterie de serveurs, utilisez la `Install-SPSolution` commande.)  
  
     Par exemple, `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.  
  
     Pour plus d’informations sur le déploiement distant, consultez [à l’aide des Solutions](http://go.microsoft.com/fwlink/?LinkId=217680) et [Ajout et déploiement de Solutions avec PowerShell dans SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d’informations sur comment personnaliser et déployer des solutions SharePoint, les rubriques suivantes :  
  
-   [Procédure pas à pas : création d’une colonne de site, d’un type de contenu et d’une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [Guide pratique pour créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [Windows PowerShell pour SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  