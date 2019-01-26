---
title: 'Procédure pas à pas : Déploiement d’une définition de liste de tâches de projet | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fd8c91389ae69e3db0125c91360df4ca0bdcdd84
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871258"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Procédure pas à pas : Déployer une définition de liste de tâches de projet

Cette procédure pas à pas explique comment créer, personnaliser, déboguer et déployer une liste SharePoint à l’aide de [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] en vue d’effectuer le suivi des tâches du projet.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis

- Éditions prises en charge de Microsoft Windows et SharePoint.

- Visual Studio 2017 ou les Services Azure DevOps.

## <a name="create-a-sharepoint-list"></a>Créer une liste SharePoint

Créez un projet de liste SharePoint et associez la définition de liste aux tâches.

1. Ouvrir le **nouveau projet** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.

2. Dans le **modèles** volet, choisissez le **projet SharePoint 2010** modèle, nommez le projet **ProjectTaskList**, puis choisissez le **OK**bouton.

     Le **Assistant Personnalisation de SharePoint** s’affiche.

3. Spécifiez le site SharePoint local que vous utilisez pour le débogage, choisissez le **déployer en tant que solution de batterie** case d’option, puis choisissez le **Terminer** bouton.

4. Ouvrez le menu contextuel du projet, puis choisissez **ajouter** > **un nouvel élément**.

5. Dans le **modèles** volet, choisissez le **liste** modèle, puis choisissez le **ajouter** bouton.

     Le **Assistant Personnalisation de SharePoint** s’affiche.

6. Dans le **quel nom voulez-vous afficher pour votre liste ?** , entrez **liste des tâches de projet**.

7. Choisissez le **créer une liste non personnalisable basée sur un type de liste existant** case d’option et, dans sa liste, choisissez **tâches**, puis choisissez le **Terminer** bouton.

     La liste, la fonctionnalité et le package s’affichent dans **l’Explorateur de solutions**.

## <a name="add-an-event-receiver"></a>Ajouter un récepteur d’événements

Dans la liste de tâches, vous pouvez ajouter un récepteur d’événements permettant de déterminer automatiquement la date d’échéance et la description de la tâche. La procédure suivante ajoute un gestionnaire d’événements simple à l’instance de liste comme un récepteur d’événements.

1. Ouvrez le menu contextuel du nœud de projet, choisissez **ajouter**, puis choisissez **un nouvel élément**.

2. Dans la liste de modèles SharePoint, choisissez le **récepteur d’événements** modèle, puis nommez-le **ProjectTaskListEventReceiver**.

     Le **Assistant Personnalisation de SharePoint** s’affiche.

3. Sur le **choisir les paramètres de récepteur d’événements** page, choisissez **événements d’élément de liste** comme type de récepteur d’événements dans le **quel type de récepteur d’événements voulez-vous** liste.

4. Dans le **quel élément doit être la source d’événements** , choisissez **tâches**.

5. Dans la liste des événements à gérer, sélectionnez la case à cocher à côté **un élément a été ajouté**, puis choisissez le **Terminer** bouton.

     Un nouveau nœud de récepteur d’événements est ajouté au projet avec un fichier de code nommé **ProjectTaskListEventReceiver**.

6. Ajoutez le code pour le `ItemAdded` méthode dans le **ProjectTaskListEventReceiver** fichier de code. Chaque fois qu’une nouvelle tâche est ajoutée, date d’échéance et une description par défaut est ajouté à la tâche. La valeur par défaut due date est le 1er juillet 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Personnaliser la fonctionnalité de liste des tâches de projet

Lorsque vous créez une solution SharePoint, Visual Studio crée automatiquement des fonctionnalités pour la valeur par défaut des éléments de projet. Vous pouvez personnaliser les paramètres de liste de tâches de projet pour le site SharePoint à l’aide du Concepteur de fonctionnalités.

1. Dans **l’Explorateur de solutions**, développez **fonctionnalités**.

2. Ouvrez le menu contextuel pour **Feature1**, puis choisissez **Concepteur de vues**.

3. Dans le **titre** , entrez **fonctionnalité liste des tâches projet**.

4. Dans le **étendue** , choisissez **Web**.

5. Dans le **propriétés** fenêtre, entrez **1.0.0.0** comme valeur pour le **Version** propriété.

## <a name="customize-the-project-task-list-package"></a>Personnaliser le package de liste de tâches de projet

Lorsque vous créez un projet SharePoint, Visual Studio ajoute automatiquement les fonctionnalités qui contiennent les éléments de projet par défaut pour le package. Vous pouvez personnaliser les paramètres de liste de tâches de projet pour le site SharePoint à l’aide du Concepteur de packages.

1. Dans **SolutionExplorer**, ouvrez le menu contextuel pour **Package**, puis choisissez **Concepteur de vues**.

2. Dans le **nom** , entrez **ProjectTaskListPackage**.

3. Sélectionnez le **réinitialiser le serveur Web** case à cocher.

## <a name="build-and-test-the-project-task-list"></a>Générer et tester la liste de tâches de projet

Lorsque vous exécutez le projet, le site SharePoint s’ouvre. Toutefois, vous devez accéder manuellement à l’emplacement de la liste des tâches.

1. Choisissez le **F5** clé pour générer et déployer votre liste de tâches de projet.

     Le site SharePoint s’ouvre.

2. Choisissez le **accueil** onglet.

3. Dans la barre latérale gauche, choisissez le **liste des tâches de projet** lien.

     La page de liste des tâches de projet s’affiche.

4. Dans le **outils de liste** , choisir le **éléments** onglet.

5. Dans le **éléments** de groupe, choisissez le **un nouvel élément** bouton.

6. Dans le **titre** texte, entrez **Task1**.

7. Choisissez le **enregistrer** bouton.

     Une fois que le site est actualisé, le **Task1** tâche apparaît avec une date d’échéance de 7/1/2009.

8. Choisissez **Task1**.

     La vue détaillée de la tâche s’affiche, et la description indique « Il s’agit d’une tâche critique. »

## <a name="deploy-the-project-task-list"></a>Déployer la liste de tâches de projet

Une fois que vous générez et testez la liste de tâches de projet, vous pouvez la déployer vers le *système local* ou un *système distant*. Le système local est le même ordinateur que celui sur lequel vous avez développé la solution, tandis qu’un système distant est un autre ordinateur.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Pour déployer la liste des tâches projet sur le système local

Dans la barre de menus de Visual Studio, choisissez **Build** > **déployer la Solution**.

Visual Studio recycle le pool d’applications IIS, retire toutes les versions existantes de la solution, copie le package de solution (*.wsp*) de fichiers sur SharePoint et ensuite activer ses fonctionnalités. Vous pouvez maintenant utiliser la solution dans SharePoint. Pour plus d’informations sur les étapes de configuration de déploiement, consultez [Comment : Modifier une configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Pour déployer la liste des tâches projet sur un système distant

1. Dans la barre de menus de Visual Studio, choisissez **Build** > **publier**.

2. Dans le **publier** boîte de dialogue, sélectionnez le **publier sur le système de fichiers** case d’option.

     Vous pouvez modifier l’emplacement cible dans le **publier** boîte de dialogue en choisissant le bouton de sélection ![icône des points de suspension](../sharepoint/media/ellipsisicon.gif "icône des points de suspension") et en accédant à un autre emplacement.

3. Choisissez le **publier** bouton.

     Un *.wsp* fichier est créé pour la solution.

4. Copie le *.wsp* fichier sur le système SharePoint distant.

5. Utilisez la commande PowerShell `Add-SPUserSolution` commande pour installer le package sur l’installation SharePoint distante. (Pour les solutions de batterie de serveurs, utilisez le `Add-SPSolution` commande.)

     Par exemple, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Utilisez la commande PowerShell `Install-SPUserSolution` commande pour déployer la solution. (Pour les solutions de batterie de serveurs, utilisez le `Install-SPSolution` commande.)

     Par exemple, `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Pour plus d’informations sur le déploiement distant, consultez [à l’aide de Solutions](http://go.microsoft.com/fwlink/?LinkId=217680) et [Ajout et déploiement de Solutions avec PowerShell dans SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur comment personnaliser et déployer des solutions SharePoint, les rubriques suivantes :

- [Procédure pas à pas : Créer une colonne de site, le type de contenu et la liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Guide pratique pour Créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)

- [PowerShell de Windows pour SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Voir aussi
[Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
