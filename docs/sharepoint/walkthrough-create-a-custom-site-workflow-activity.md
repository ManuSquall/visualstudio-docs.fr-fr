---
title: 'Procédure pas à pas : créer une activité de flux de travail de site personnalisée | Microsoft Docs'
description: Dans cette procédure pas à pas, consultez Comment créer une activité personnalisée pour un flux de travail SharePoint au niveau du site à l’aide de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29a3cd6fe37ec824a3db3a2c83aad7434d0018cb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218046"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Procédure pas à pas : créer une activité de flux de travail de site personnalisé
  Cette procédure pas à pas montre comment créer une activité personnalisée pour un flux de travail au niveau du site à l’aide de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . (Les flux de travail au niveau du site s’appliquent à l’ensemble du site, pas seulement à une liste sur le site.) L’activité personnalisée crée une liste d’annonces de sauvegarde et y copie le contenu de la liste d’annonces.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un flux de travail au niveau du site.

- Création d’une activité de flux de travail personnalisée.

- Création et suppression d’une liste SharePoint.

- Copie d’éléments d’une liste à une autre.

- Affichage d’une liste sur la barre de lancement rapide.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.

- Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>Créer un projet d’activité personnalisée de flux de travail de site
 Tout d’abord, créez un projet pour stocker et tester l’activité de flux de travail personnalisée.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Pour créer un projet d’activité personnalisée de flux de travail de site

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** pour afficher la boîte de dialogue **nouveau projet** .

2. Développez le nœud **SharePoint** sous **Visual C#** ou **Visual Basic**, puis choisissez le nœud **2010** .

3. Dans le volet **modèles** , choisissez le modèle de **projet SharePoint 2010** .

4. Dans la zone **nom** , entrez **AnnouncementBackup**, puis choisissez le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.

5. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , choisissez la case **d’option déployer en tant que solution de batterie** , puis choisissez le bouton **Terminer** pour accepter le niveau de confiance et le site par défaut.

     Cette étape définit le niveau de confiance de la solution en tant que solution de batterie de serveurs, la seule option disponible pour les projets de Workflow.

6. Dans **Explorateur de solutions**, choisissez le nœud de projet, puis, dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

7. Sous **Visual C#** ou **Visual Basic**, développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

8. Dans le volet **modèles** , choisissez le modèle **Workflow séquentiel (solution de batterie uniquement)** , puis cliquez sur le bouton **Ajouter** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.

9. Dans la page **spécifier le nom du flux de travail pour le débogage** , acceptez le nom par défaut (AnnouncementBackup-Workflow1). Modifiez le type de modèle de flux de travail en **Workflow de site**, puis cliquez sur le bouton **suivant** .

10. Choisissez le bouton **Terminer** pour accepter les paramètres par défaut restants.

## <a name="add-a-custom-workflow-activity-class"></a>Ajouter une classe d’activité de flux de travail personnalisée
 Ensuite, ajoutez une classe au projet pour contenir le code de l’activité de flux de travail personnalisée.

#### <a name="to-add-a-custom-workflow-activity-class"></a>Pour ajouter une classe d’activité de flux de travail personnalisée

1. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément** pour afficher la boîte de dialogue **Ajouter un nouvel élément** .

2. Dans l’arborescence **modèles installés** , choisissez le nœud **code** , puis choisissez le modèle de **classe** dans la liste des modèles d’élément de projet. Utilisez le nom par défaut Class1. Choisissez le bouton **Ajouter**.

3. Remplacez tout le code de Class1 par ce qui suit :

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb" id="Snippet1":::

4. Enregistrez le projet, puis, dans la barre de menus, choisissez **générer**  >  **générer la solution**.

     Class1 apparaît en tant qu’action personnalisée dans la **boîte à outils** sous l’onglet **composants AnnouncementBackup** .

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Ajouter l’activité personnalisée au flux de travail de site
 Ensuite, ajoutez une activité au flux de travail pour contenir le code personnalisé.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Pour ajouter une activité personnalisée au workflow de site

1. Ouvrez Workflow1 dans le concepteur de flux de travail en mode Design.

2. Faites glisser classe1 de la **boîte à outils** pour qu’elle apparaisse sous l' `onWorkflowActivated1` activité, ou ouvrez le menu contextuel de Class1, choisissez **copier**, ouvrez le menu contextuel de la ligne sous l' `onWorkflowActivated1` activité, puis choisissez **coller**.

3. Enregistrez le projet.

## <a name="test-the-site-workflow-custom-activity"></a>Tester l’activité personnalisée de flux de travail de site
 Ensuite, exécutez le projet et démarrez le flux de travail du site. L’activité personnalisée crée une liste d’annonces de sauvegarde et y copie le contenu de la liste d’annonces actuelle. Le code vérifie également si une liste de sauvegarde existe déjà avant d’en créer une. Si une liste de sauvegarde existe déjà, elle est supprimée. Le code ajoute également un lien vers la nouvelle liste dans la barre de lancement rapide du site SharePoint.

#### <a name="to-test-the-site-workflow-custom-activity"></a>Pour tester l’activité personnalisée de flux de travail de site

1. Appuyez sur la touche **F5** pour exécuter le projet et le déployer sur SharePoint.

2. Dans la barre de lancement rapide, choisissez le lien **listes** pour afficher toutes les listes disponibles sur le site SharePoint. Notez qu’il n’existe qu’une seule liste pour les annonces nommées **annonces**.

3. En haut de la page Web SharePoint, choisissez le lien **flux de travail de site** .

4. Sous la section Démarrer un nouveau flux de travail, choisissez le lien **AnnouncementBackup-Workflow1** . Cela démarre le flux de travail du site et exécute le code dans l’action personnalisée.

5. Dans la barre de lancement rapide, choisissez le lien de **sauvegarde annonces** . Notez que toutes les annonces contenues dans la liste **annonces** ont été copiées dans cette nouvelle liste.

## <a name="see-also"></a>Voir aussi
- [Comment : créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
