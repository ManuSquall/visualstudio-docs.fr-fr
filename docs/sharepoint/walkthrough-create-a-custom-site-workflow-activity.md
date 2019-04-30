---
title: 'Procédure pas à pas : Créer une activité de flux de travail de Site personnalisé | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f717345689de9be640e03e9c7d81726a57d494b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008317"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Procédure pas à pas : Créer une activité de flux de travail de site personnalisée
  Cette procédure pas à pas montre comment créer une activité personnalisée pour un flux de travail au niveau du site à l’aide [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Flux de travail au niveau du site s’appliquent à l’ensemble du site, pas seulement une liste sur le site). L’activité personnalisée crée une liste d’annonces de sauvegarde, puis copie le contenu de la liste d’annonces dedans.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un flux de travail au niveau du site.

- Création d’une activité de flux de travail personnalisé.

- Création et suppression d’une liste SharePoint.

- Copie les éléments d’une liste à un autre.

- Affichage d’une liste dans la barre de lancement rapide.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Éditions prises en charge [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.

- Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>Créer un projet d’activité personnalisée de flux de travail site
 Tout d’abord, créez un projet pour contenir et de tester l’activité de flux de travail personnalisé.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Pour créer un projet d’activité personnalisée de flux de travail site

1. Dans la barre de menus, choisissez **fichier** > **New** > **projet** pour afficher le **nouveau projet** boîte de dialogue.

2. Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez le **2010** nœud.

3. Dans le **modèles** volet, choisissez le **projet SharePoint 2010** modèle.

4. Dans le **nom** , entrez **SauvegardeAnnonces**, puis choisissez le **OK** bouton.

     Le **Assistant Personnalisation de SharePoint** s’affiche.

5. Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, choisissez le **déployer en tant que solution de batterie** case d’option, puis choisissez le **Terminer** bouton pour accepter le site par défaut et le niveau de confiance.

     Cette étape définit le niveau de confiance pour la solution en tant que solution de batterie de serveurs, la seule option disponible pour les projets de flux de travail.

6. Dans **l’Explorateur de solutions**, choisissez le nœud du projet, puis, dans la barre de menus, choisissez **projet** > **ajouter un nouvel élément**.

7. Sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.

8. Dans le **modèles** volet, choisissez le **Workflow séquentiel (Solution de batterie uniquement)** modèle, puis choisissez le **ajouter** bouton.

     Le **Assistant Personnalisation de SharePoint** s’affiche.

9. Sur le **spécifier le nom de flux de travail pour le débogage** page, acceptez le nom par défaut (SauvegardeAnnonces - Workflow1). Modifiez le type de modèle de flux de travail **Site Workflow**, puis choisissez le **suivant** bouton.

10. Choisissez le **Terminer** bouton pour accepter les paramètres par défaut restantes.

## <a name="add-a-custom-workflow-activity-class"></a>Ajouter une classe d’activité de flux de travail personnalisé
 Ensuite, ajoutez une classe au projet pour contenir le code de l’activité de flux de travail personnalisé.

#### <a name="to-add-a-custom-workflow-activity-class"></a>Pour ajouter une classe d’activité de flux de travail personnalisé

1. Dans la barre de menus, choisissez **projet** > **ajouter un nouvel élément** pour afficher le **ajouter un nouvel élément** boîte de dialogue.

2. Dans le **modèles installés** vue arborescente, choisissez le **Code** nœud, puis choisissez le **classe** modèle dans la liste des modèles d’élément de projet. Utilisez le nom par défaut Class1. Choisissez le bouton **Ajouter** .

3. Remplacez tout le code dans Class1 avec les éléments suivants :

     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]

4. Enregistrez le projet et puis, dans la barre de menus, choisissez **Build** > **générer la Solution**.

     Class1 apparaît sous la forme d’une action personnalisée dans le **boîte à outils** sur le **SauvegardeAnnonces composants** onglet.

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Ajouter l’activité personnalisée au flux de travail de site
 Ensuite, ajoutez une activité au flux de travail pour contenir le code personnalisé.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Pour ajouter une activité personnalisée au flux de travail de site

1. Ouvrez Workflow1 dans le Concepteur de flux de travail en mode conception.

2. Faites glisser Class1 à partir de la **boîte à outils** afin qu’il apparaisse sous le `onWorkflowActivated1` activité, ou ouvrez le menu contextuel pour Class1, choisissez **copie**, ouvrez le menu contextuel pour la ligne sous la `onWorkflowActivated1` activité, puis choisissez **coller**.

3. Enregistrez le projet.

## <a name="test-the-site-workflow-custom-activity"></a>Tester l’activité personnalisée de flux de travail de site
 Ensuite, exécutez le projet et démarrer le flux de travail de site. L’activité personnalisée crée une liste d’annonces sauvegarde et copie le contenu dans la liste des annonces dedans. Le code vérifie également si une liste de sauvegarde existe déjà avant de créer une. Si une liste de sauvegarde existe déjà, elle est supprimée. Le code ajoute également un lien vers la nouvelle liste sur la barre de lancement rapide du site SharePoint.

#### <a name="to-test-the-site-workflow-custom-activity"></a>Pour tester l’activité personnalisée de flux de travail de site

1. Choisissez le **F5** clé pour exécuter le projet et le déployer sur SharePoint.

2. Dans la barre de lancement rapide, choisissez le **répertorie** lien pour afficher toutes les listes qui sont disponibles dans le site SharePoint. Notez qu’une seule liste pour les annonces appelée **annonces**.

3. En haut de la page Web de SharePoint, choisissez le **des flux de travail Site** lien.

4. Sous le début une section de nouveau flux de travail, choisissez la **SauvegardeAnnonces - Workflow1** lien. Cela démarre le workflow de site et exécute le code de l’action personnalisée.

5. Dans la barre de lancement rapide, choisissez le **annonces sauvegarde** lien. Notez que toutes les annonces qui sont contenus dans le **annonces** liste ont été copiés vers cette nouvelle liste.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
