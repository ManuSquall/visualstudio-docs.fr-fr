---
title: 'Procédure pas à pas : déploiement d’une définition de Liste des tâches de projet | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: b5639fe7a1b35dea41b14be3730986ad7c7309b7
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015769"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Procédure pas à pas : déployer une définition de liste de tâches de projet

Cette procédure pas à pas explique comment créer, personnaliser, déboguer et déployer une liste SharePoint à l’aide de [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] en vue d’effectuer le suivi des tâches du projet.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis

- Éditions prises en charge de Microsoft Windows et SharePoint.

- Visual Studio 2017 ou Azure DevOps Services.

## <a name="create-a-sharepoint-list"></a>Créer une liste SharePoint

Créez un projet de liste SharePoint et associez la définition de liste aux tâches.

1. Ouvrez la boîte **de dialogue Nouveau projet** , développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

2. Dans le volet **modèles** , choisissez le modèle de **projet SharePoint 2010** , nommez le projet **ProjectTaskList**, puis choisissez le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.

3. Spécifiez le site SharePoint local que vous utilisez pour le débogage, sélectionnez la case d’option **déployer en tant que solution de batterie** , puis cliquez sur le bouton **Terminer** .

4. Ouvrez le menu contextuel du projet, puis choisissez **Ajouter**  >  **un nouvel élément**.

5. Dans le volet **modèles** , choisissez le modèle de **liste** , puis cliquez sur le bouton **Ajouter** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.

6. Dans la zone **quel nom voulez-vous afficher pour votre liste ?** , entrez **Project liste des tâches**.

7. Sélectionnez la case **d’option créer une liste non personnalisable basée sur un type de liste existant** , puis, dans la liste, choisissez **tâches**, puis cliquez sur le bouton **Terminer** .

     La liste, la fonctionnalité et le package s’affichent dans **Explorateur de solutions**.

## <a name="add-an-event-receiver"></a>Ajouter un récepteur d’événements

Dans la liste de tâches, vous pouvez ajouter un récepteur d’événements permettant de déterminer automatiquement la date d’échéance et la description de la tâche. La procédure suivante ajoute un gestionnaire d’événements simple à l’instance de liste en tant que récepteur d’événements.

1. Ouvrez le menu contextuel du nœud de projet, choisissez **Ajouter**, puis **nouvel élément**.

2. Dans la liste des modèles SharePoint, choisissez le modèle **récepteur d’événements** , puis nommez-le **ProjectTaskListEventReceiver**.

     L' **Assistant Personnalisation de SharePoint** s’affiche.

3. Sur la page **choisir les paramètres de récepteur d’événements** , choisissez liste des événements d' **élément** comme type de récepteur d’événements dans la liste **quel type de récepteur d’événements voulez-vous** .

4. Dans la liste **quel élément doit être la source d’événement** , choisissez **tâches**.

5. Dans la liste des événements à gérer, activez la case à cocher en regard d' **un élément a été ajouté**, puis choisissez le bouton **Terminer** .

     Un nouveau nœud récepteur d’événements est ajouté au projet avec un fichier de code nommé **ProjectTaskListEventReceiver**.

6. Ajoutez du code à la `ItemAdded` méthode dans le fichier de code **ProjectTaskListEventReceiver** . Chaque fois qu’une nouvelle tâche est ajoutée, une date d’échéance par défaut et une description sont ajoutées à la tâche. La date d’échéance par défaut est le 1er juillet 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Personnaliser la fonctionnalité de liste des tâches du projet

Quand vous créez une solution SharePoint, Visual Studio crée automatiquement des fonctionnalités pour les éléments de projet par défaut. Vous pouvez personnaliser les paramètres de liste des tâches de projet pour le site SharePoint à l’aide du concepteur de fonctionnalités.

1. Dans **Explorateur de solutions**, développez **fonctionnalités**.

2. Ouvrez le menu contextuel pour **Feature1**, puis choisissez **Concepteur de vues**.

3. Dans la zone **titre** , entrez **Project liste des tâches fonctionnalité**.

4. Dans la liste **étendue** , choisissez **Web**.

5. Dans la fenêtre **Propriétés** , entrez **1.0.0.0** comme valeur pour la propriété **version** .

## <a name="customize-the-project-task-list-package"></a>Personnaliser le package de liste des tâches du projet

Lorsque vous créez un projet SharePoint, Visual Studio ajoute automatiquement les fonctionnalités qui contiennent les éléments de projet par défaut au package. Vous pouvez personnaliser les paramètres de liste des tâches de projet pour le site SharePoint à l’aide du concepteur de packages.

1. Dans **SolutionExplorer**, ouvrez le menu contextuel du **package**, puis choisissez **Concepteur de vues**.

2. Dans la zone **nom** , entrez **ProjectTaskListPackage**.

3. Activez la case à cocher **Réinitialiser le serveur Web** .

## <a name="build-and-test-the-project-task-list"></a>Générer et tester la liste des tâches du projet

Lorsque vous exécutez le projet, le site SharePoint s’ouvre. Toutefois, vous devez accéder manuellement à l’emplacement de la liste des tâches.

1. Appuyez sur la touche **F5** pour générer et déployer votre liste des tâches de projet.

     Le site SharePoint s’ouvre.

2. Choisissez l’onglet dossier de **démarrage** .

3. Dans le volet gauche, choisissez le lien **liste des tâches du projet** .

     La page Liste des tâches du projet s’affiche.

4. Sous l’onglet **outils de liste** , choisissez l’onglet **éléments** .

5. Dans le groupe **éléments** , cliquez sur le bouton **nouvel élément** .

6. Dans la zone de texte **titre** , entrez **Task1**.

7. Choisissez le bouton **Enregistrer** .

     Une fois le site actualisé, la tâche **Task1** s’affiche avec une date d’échéance de 7/1/2009.

8. Choisissez **Task1**.

     La vue détaillée de la tâche s’affiche et la description indique « il s’agit d’une tâche critique ».

## <a name="deploy-the-project-task-list"></a>Déployer la liste des tâches du projet

Après avoir généré et testé la liste des tâches du projet, vous pouvez la déployer sur le *système local* ou sur un *système distant*. Le système local est le même ordinateur que celui sur lequel vous avez développé la solution, alors qu’un système distant est un ordinateur différent.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Pour déployer la liste des tâches de projet sur le système local

Dans la barre de menus de Visual Studio, choisissez **générer**  >  **déployer la solution**.

Visual Studio recycle le pool d’applications IIS, retire toutes les versions existantes de la solution, copie le fichier de package de solution (*. wsp*) vers SharePoint, puis active ses fonctionnalités. Vous pouvez maintenant utiliser la solution dans SharePoint. Pour plus d’informations sur les étapes de configuration du déploiement, consultez [procédure : modifier une configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Pour déployer la liste des tâches de projet sur un système distant

1. Dans la barre de menus de Visual Studio, choisissez **générer**  >  **publier**.

2. Dans la boîte de dialogue **publier** , choisissez la case **d’option publier sur le système de fichiers** .

     Vous pouvez modifier l’emplacement cible dans la boîte de dialogue **publier** en cliquant sur l' ![icône de sélection](../sharepoint/media/ellipsisicon.gif "Icône du bouton de sélection (...)") du bouton de sélection, puis en accédant à un autre emplacement.

3. Choisissez le bouton **Publier**.

     Un fichier *. wsp* est créé pour la solution.

4. Copiez le fichier *. wsp* dans le système SharePoint distant.

5. Utilisez la `Add-SPUserSolution` commande PowerShell pour installer le package sur l’installation SharePoint distante. (Pour les solutions de batterie de serveurs, utilisez la `Add-SPSolution` commande.)

     Par exemple : `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Utilisez la `Install-SPUserSolution` commande PowerShell pour déployer la solution. (Pour les solutions de batterie de serveurs, utilisez la `Install-SPSolution` commande.)

     Par exemple : `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Pour plus d’informations sur le déploiement à distance, consultez [utilisation de solutions](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) et [Ajout et déploiement de solutions avec PowerShell dans SharePoint 2010](http://www.dotnetmafia.com/blogs/dotnettipoftheday/archive/2009/12/02/adding-and-deploying-solutions-with-powershell-in-sharepoint-2010.aspx).

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez en savoir plus sur la personnalisation et le déploiement des solutions SharePoint à partir des rubriques suivantes :

- [Procédure pas à pas : création d’une colonne de site, d’un type de contenu et d’une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Comment : créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell pour SharePoint Server 2010](/powershell/module/sharepoint-server)

## <a name="see-also"></a>Voir aussi
[Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
