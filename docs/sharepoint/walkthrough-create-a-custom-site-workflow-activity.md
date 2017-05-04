---
title: "Proc&#233;dures pas &#224; pas&#160;: cr&#233;ation d&#39;une activit&#233; de workflow de site personnalis&#233;e | Microsoft Docs"
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
  - "activités de flux de travail personnalisées (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, activités de flux de travail personnalisées"
  - "développement SharePoint dans Visual Studio, flux de travail de site"
  - "flux de travail de site (développement SharePoint dans Visual Studio)"
  - "activités de flux de travail (développement SharePoint dans Visual Studio)"
ms.assetid: 8219a779-c27b-4186-92c9-5bda03328aa9
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Proc&#233;dures pas &#224; pas&#160;: cr&#233;ation d&#39;une activit&#233; de workflow de site personnalis&#233;e
  Cette procédure pas à pas montre comment créer une activité personnalisée pour un flux de travail au niveau du site à l'aide de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Les flux de travail au niveau du site s'appliquent au site entier et pas uniquement à une liste du site. L'activité personnalisée crée une liste Annonces de sauvegarde, puis y copie le contenu de la liste Annonces.  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'un flux de travail au niveau du site.  
  
-   Création d'une activité de flux de travail personnalisée.  
  
-   Création et suppression d'une liste SharePoint.  
  
-   Copie des éléments d'une liste à une autre.  
  
-   Affichage d'une liste dans la barre d'outils Lancement rapide.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et de SharePoint prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Création d'un projet d'activité de flux de travail personnalisée au niveau du site  
 Commencez par créer le projet réservé au stockage et au test de l'activité de flux de travail personnalisée.  
  
#### Pour créer un projet d'activité de flux de travail personnalisée au niveau du site  
  
1.  Dans la barre de menus, choisissez **Fichier**, **Nouveau**, **Projet** pour afficher la boîte de dialogue **Nouveau projet**.  
  
2.  Développez le nœud **SharePoint** sous **Visual C\#** ou **Visual Basic**, puis cliquez sur le noeud **2010**.  
  
3.  Dans le volet de **Modèles**, sélectionnez le modèle **Projet SharePoint 2010**.  
  
4.  Dans la zone de texte **Nom**, entrez AnnouncementBackup, puis cliquez sur le bouton **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
5.  Sur la page **Spécifier le site et le niveau de sécurité pour le débogage**, sélectionnez la case d'option **Déployer en tant que solution de batterie**, puis cliquez sur le bouton **Terminer** pour accepter le niveau de confiance et le site par défaut.  
  
     Cette étape définit le niveau de confiance de la solution en considérant qu'il s'agit d'une solution de la batterie, la seule option disponible pour les projets de flux de travail.  
  
6.  Dans l'**Explorateur de solutions**, choisissez le nœud de projet, puis, dans la barre de menus, choisissez **Project**, **Ajouter un nouvel objet**.  
  
7.  Sous **Visual C\#** ou **Visual Basic**, développez le nœud **SharePoint**, puis cliquez sur le noeud **2010**.  
  
8.  Dans le volet **Modèles**, sélectionnez le modèle **Flux de travail séquentiel \(solution de batterie uniquement\)**, puis cliquez sur le bouton **Ajouter**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
9. Sur la page **Spécifier le nom du flux de travail pour le débogage**, acceptez le nom proposé par défaut \(SauvegardeAnnonces \- Workflow1\).  Remplacez le type de modèle de flux de travail par **Flux de travail de site**, puis cliquez sur le bouton**Suivant**.  
  
10. Cliquez sur le bouton **Terminer** pour accepter les paramètres par défaut restants.  
  
## Ajout d'une classe d'activité de flux de travail personnalisée  
 Ajoutez ensuite une classe au projet afin d'y enregistrer le code de l'activité de flux de travail personnalisée.  
  
#### Pour ajouter une classe d'activité de flux de travail personnalisée  
  
1.  Sur la barre de menu, cliquez sur **ProjetAjouter un nouvel élément** pour afficher la boîte de dialogue **Ajouter un nouvel élément**.  
  
2.  Dans l'arborescence **Modèles installés**, cliquez sur le nœud **Code**, puis sur **Classe** dans la liste des modèles d'élément de projet.  Employez le nom par défaut Class1.  Choisissez le bouton **Ajouter**.  
  
3.  Remplacez l'intégralité du code dans Class1 par le code suivant :  
  
     [!code-csharp[SP_AnnBackup#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_annbackup/cs/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_annbackup/vb/class1.vb#1)]  
  
4.  Enregistrez le projet puis, dans la barre de menu, cliquez sur **Générer**, **Générer la solution**.  
  
     Class1 apparaît en tant qu'action personnalisée dans la **Boîte à outils** sous l'onglet de **Composants d'AnnouncementBackup**.  
  
## Ajout de l'activité personnalisée au flux de travail de site  
 Ajoutez, à présent, une activité au flux de travail afin d'y inclure le code personnalisé.  
  
#### Pour ajouter une activité personnalisée au flux de travail de site  
  
1.  Ouvrez Workflow1 dans le Concepteur de flux de travail en mode Design.  
  
2.  Faites glisser Class1 depuis la **Boîte à outils** afin qu'il s'affiche dans l'activité de `onWorkflowActivated1`, ou ouvrir le menu contextuel de Class1, choisissez **Copier**, ouvrez le menu contextuel de la ligne dans l'activité de `onWorkflowActivated1`, puis choisissez **Coller**.  
  
3.  Enregistrez le projet.  
  
## Test de l'activité de flux de travail personnalisée au niveau du site  
 Exécutez le projet et démarrez le flux de travail de site.  L'activité personnalisée crée une liste Annonces de sauvegarde, puis y copie le contenu de la liste Annonces actuelle.  Le code vérifie, au préalable, s'il existe déjà une liste de sauvegarde avant d'en créer une  et la supprime le cas échéant.  Le code ajoute également un lien à la nouvelle liste dans la barre de lancement rapide du site SharePoint.  
  
#### Pour tester l'activité de flux de travail personnalisée au niveau du site  
  
1.  Appuyez sur la touche F5 pour exécuter le projet et le déployer sur SharePoint.  
  
2.  Cliquez sur **Listes** dans la barre de lancement rapide pour afficher toutes les listes disponibles sur le site SharePoint.  Vous pouvez remarquer qu'il existe une seule liste pour les annonces appelée **Annonces**.  
  
3.  En haut de la page Web SharePoint, choisissez le lien **Workflows de site**.  
  
4.  Dans la section Démarrer un nouveau flux de travail, cliquez sur le lien **AnnouncementBackup – Workflow1**.  afin de lancer le flux de travail de site et d'exécuter le code de l'action personnalisée.  
  
5.  Dans la barre de démarrage rapide, sélectionnez le lien **Annonces de sauvegarde**.  Notez que toutes les annonces figurant dans la liste **Annonces** ont été copiées dans cette nouvelle liste.  
  
## Voir aussi  
 [Comment : créer un récepteur d'événements](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  