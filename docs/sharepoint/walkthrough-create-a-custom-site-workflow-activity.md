---
title: "Procédure pas à pas : Création d’une activité de flux de travail de Site personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
ms.assetid: 8219a779-c27b-4186-92c9-5bda03328aa9
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b7a24c793755cdd5102407d1a3a5cbfad103c92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Procédures pas à pas : création d'une activité de workflow de site personnalisée
  Cette procédure pas à pas montre comment créer une activité personnalisée pour un flux de travail au niveau du site à l’aide de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Flux de travail au niveau du site s’appliquent à l’ensemble du site, pas seulement une liste sur le site.) L’activité personnalisée crée une liste d’annonces de sauvegarde, puis copie le contenu de la liste d’annonces dans celui-ci.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un flux de travail au niveau du site.  
  
-   Création d’une activité de flux de travail personnalisé.  
  
-   Création et suppression d’une liste SharePoint.  
  
-   Copie les éléments d’une liste vers un autre.  
  
-   Affiche la liste dans la barre de lancement rapide.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-site-workflow-custom-activity-project"></a>Création d’un projet d’activité personnalisée de flux de travail Site  
 Commencez par créer un projet pour le stockage et de tester l’activité de flux de travail personnalisé.  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Pour créer un projet d’activité personnalisée de flux de travail site  
  
1.  Dans la barre de menus, choisissez **fichier**, **nouveau**, **projet** pour afficher les **nouveau projet** boîte de dialogue.  
  
2.  Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez le **2010** nœud.  
  
3.  Dans le **modèles** volet, choisissez la **projet SharePoint 2010** modèle.  
  
4.  Dans le **nom** , entrez **SauvegardeAnnonces**, puis choisissez le **OK** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
5.  Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, choisissez la **déployer une solution de batterie de serveurs** case d’option, puis choisissez le **Terminer** bouton pour accepter le site par défaut et le niveau de confiance.  
  
     Cette étape définit le niveau de confiance de la solution en tant que solution de batterie, la seule option disponible pour les projets de flux de travail.  
  
6.  Dans **l’Explorateur de solutions**, choisissez le nœud du projet, puis, dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
7.  Sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
8.  Dans le **modèles** volet, choisissez la **Workflow séquentiel (Solution de batterie uniquement)** modèle, puis choisissez le **ajouter** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
9. Sur le **spécifier le nom de flux de travail pour le débogage** page, acceptez le nom par défaut (SauvegardeAnnonces - Workflow1). Modifier le type de modèle de flux de travail à **Site Workflow**, puis choisissez le **suivant** bouton.  
  
10. Choisissez le **Terminer** bouton pour accepter les paramètres par défaut restantes.  
  
## <a name="adding-a-custom-workflow-activity-class"></a>Ajout d’une classe d’activité de flux de travail personnalisé  
 Ensuite, ajoutez une classe au projet pour contenir le code de l’activité de flux de travail personnalisé.  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>Pour ajouter une classe d’activité de flux de travail personnalisé  
  
1.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément** pour afficher les **ajouter un nouvel élément** boîte de dialogue.  
  
2.  Dans le **modèles installés** vue arborescente, choisissez le **Code** nœud, puis choisissez le **classe** modèle dans la liste des modèles d’élément de projet. Utilisez le nom par défaut Class1. Choisissez le bouton **Ajouter** .  
  
3.  Remplacez tout le code dans Class1 avec les éléments suivants :  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  Enregistrez le projet, puis, dans la barre de menus, choisissez **générer**, **générer la Solution**.  
  
     Class1 apparaît sous la forme d’une action personnalisée dans le **boîte à outils** sur la **SauvegardeAnnonces composants** onglet.  
  
## <a name="adding-the-custom-activity-to-the-site-workflow"></a>Ajout de l’activité personnalisée au flux de travail de Site  
 Ensuite, ajoutez une activité au flux de travail pour contenir le code personnalisé.  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Pour ajouter une activité personnalisée pour le flux de travail de site  
  
1.  Ouvrez Workflow1 dans le Concepteur de flux de travail en mode Création.  
  
2.  Faites glisser Class1 à partir de la **boîte à outils** afin qu’il apparaisse sous le `onWorkflowActivated1` activité, ou ouvrez le menu contextuel de Class1, choisissez **copie**, ouvrez le menu contextuel de la ligne dans le `onWorkflowActivated1` activité, puis choisissez **coller**.  
  
3.  Enregistrez le projet.  
  
## <a name="testing-the-site-workflow-custom-activity"></a>Test de l’activité personnalisée de flux de travail de Site  
 Ensuite, exécutez le projet et démarrer le flux de travail de site. L’activité personnalisée crée une sauvegarde de la liste Annonces et copie le contenu à partir de la liste d’annonces en cours au. Le code vérifie également si une liste de sauvegarde existe déjà avant de le créer. Si une liste de sauvegarde existe déjà, il est supprimé. Le code ajoute également un lien vers la nouvelle liste sur la barre de lancement rapide du site SharePoint.  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>Pour tester l’activité personnalisée de flux de travail de site  
  
1.  Choisissez la touche F5 pour exécuter le projet et le déployer sur SharePoint.  
  
2.  Dans la barre de lancement rapide, choisissez le **répertorie** lien pour afficher toutes les listes qui sont disponibles dans le site SharePoint. Notez qu’une seule liste pour les annonces appelée **annonces**.  
  
3.  En haut de la page Web de SharePoint, choisissez le **flux de travail de Site** lien.  
  
4.  Sous le début une section nouveau flux de travail, choisissez la **SauvegardeAnnonces - Workflow1** lien. Cela démarre le flux de travail de site et exécute le code de l’action personnalisée.  
  
5.  Dans la barre de lancement rapide, choisissez le **annonces sauvegarde** lien. Notez que toutes les annonces qui figurent dans le **annonces** liste ont été copiés vers cette nouvelle liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)   
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  