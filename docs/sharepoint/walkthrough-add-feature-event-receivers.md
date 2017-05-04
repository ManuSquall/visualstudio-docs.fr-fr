---
title: "Proc&#233;dure pas &#224; pas&#160;: ajout de r&#233;cepteurs d&#39;&#233;v&#233;nements de fonctionnalit&#233; | Microsoft Docs"
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
  - "développement SharePoint dans Visual Studio, outils d'empaquetage avancés"
  - "développement SharePoint dans Visual Studio, récepteurs d'événements"
  - "développement SharePoint dans Visual Studio, récepteurs d'événements de fonctionnalité"
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Proc&#233;dure pas &#224; pas&#160;: ajout de r&#233;cepteurs d&#39;&#233;v&#233;nements de fonctionnalit&#233;
  Les récepteurs d'événements de fonctionnalité sont des méthodes prévues pour s'exécuter lorsque l'un des événements suivants ayant trait aux fonctionnalités se produit dans SharePoint :  
  
-   Installation d'une fonctionnalité.  
  
-   Activation d'une fonctionnalité.  
  
-   Désactivation d'une fonctionnalité.  
  
-   Suppression d'une fonctionnalité.  
  
 Cette procédure pas à pas montre comment ajouter un récepteur d'événements à une fonctionnalité dans un projet SharePoint.  Elle prend en compte les tâches suivantes :  
  
-   Création d'un projet vide avec un récepteur d'événements de fonctionnalité.  
  
-   Gestion de la méthode **FeatureDeactivating**.  
  
-   Utilisation du modèle d'objet du projet SharePoint pour ajouter une annonce à la liste Annonces.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de Microsoft Windows et SharePoint prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Création d'un projet pour un récepteur d'événements de fonctionnalité  
 Commencez par créer un projet destiné à contenir le récepteur d'événements de fonctionnalité.  
  
#### Pour créer un projet avec un récepteur d'événements de fonctionnalité  
  
1.  Dans la barre de menus, choisissez **Fichier**, **Nouveau**, **Projet** pour afficher la boîte de dialogue **Nouveau projet**.  
  
2.  Développez le nœud **SharePoint** sous **Visual C\#** ou **Visual Basic**, puis cliquez sur le noeud **2010**.  
  
3.  Dans le volet de **Modèles**, sélectionnez le modèle **Projet SharePoint 2010**.  
  
     Ce type de projet est destiné aux récepteurs d'événements de fonctionnalité, car il n'existe pas de modèle de projet pour eux.  
  
4.  Dans la zone **Nom**, tapez TestÉvénementFonctionnalité, puis cliquez sur **OK** pour afficher l'**Assistant Personnalisation de SharePoint**.  
  
5.  Dans la page **Spécifier le site et le niveau de sécurité pour le débogage**, entrez l'URL du site de serveur SharePoint auquel vous souhaitez ajouter le nouvel élément de champ personnalisé ou utilisez l'emplacement par défaut \(http:\/\/\<*system name*\>\/\).  
  
6.  Dans la section **Quel est le niveau de confiance de cette solution SharePoint ?**, choisissez la case d'option **Déployer en tant que solution de batterie**.  
  
     Pour plus d'informations sur les différences entre les solutions bac à sable \(sandbox\) et les solutions de batterie, consultez [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Cliquez sur le bouton **Terminer**, puis notez qu'une fonctionnalité appelée Feature1 apparaît sous le nœud **Fonctionnalités**.  
  
## Ajout d'un récepteur d'événements à la fonctionnalité  
 Il convient maintenant d'ajouter un récepteur d'événements à la fonctionnalité et de prévoir le code à exécuter en cas de désactivation de la fonctionnalité.  
  
#### Pour ajouter un récepteur d'événements à la fonctionnalité  
  
1.  Ouvrir le menu contextuel du noeud des composants, puis choisissez **Ajouter un composant** pour créer un composant.  
  
2.  Sous le nœud **Composants**, ouvrez le menu contextuel de **Feature1**, puis choisissez **Ajouter un récepteur d'événements** pour ajouter un récepteur d'événements aux fonctionnalités.  
  
     Cela permet d'insérer un fichier de code sous Feature1.  Dans le cas présent, il est nommé Feature1.EventReceiver.cs ou Feature1.EventReceiver.vb, selon le langage de développement de votre projet.  
  
3.  Si votre projet est écrit dans [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], ajoutez le code suivant en haut du récepteur d'événements s'il n'y est pas déjà :  
  
     [!code-csharp[SP_FeatureEvt#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  La classe de récepteur d'événements contient plusieurs méthodes commentées se comportant comme des événements.  Remplacez la méthode **FeatureDeactivating** par la méthode suivante :  
  
     [!code-csharp[SP_FeatureEvt#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#2)]
     [!code-vb[SP_FeatureEvt#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_featureevt/vb/features/feature1/feature1.eventreceiver.vb#2)]  
  
## Test du récepteur d'événements de la fonctionnalité  
 Veuillez à présent désactiver la fonctionnalité pour tester si la méthode **FeatureDeactivating** produit une annonce dans la liste des annonces SharePoint.  
  
#### Pour tester le récepteur d'événements de la fonctionnalité  
  
1.  Affectez à la propriété **Configuration de déploiement active** du projet, la valeur **Aucune activation**.  
  
     Cela empêche l'activation de la fonctionnalité dans SharePoint et vous permet de déboguer les récepteurs d'événements de la fonctionnalité.  Pour plus d'informations, consultez [Débogage de solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Appuyez sur la touche **F5** pour exécuter le projet et le déployer sur SharePoint.  
  
3.  En haut de la page Web SharePoint, ouvrez le menu **Actions du site**, puis cliquez sur **Paramètres du site**.  
  
4.  Dans la section **Actions du site** de la page **Paramètres du site**, cliquez sur le lien **Gérer les fonctionnalités du site**.  
  
5.  Dans la page **Fonctionnalités du site**, cliquez sur le bouton **Activer** en regard de la fonctionnalité **TestÉvénementFonctionnalité Feature1**.  
  
6.  Dans la page **Composants**, cliquez sur le bouton **Désactiver** à côté du composant **FeatureEvtTest Feature1**, puis sélectionnez le lien de confirmation **Désactiver ce composant** pour désactiver le composant.  
  
7.  Choisissez le bouton **Accueil**.  
  
     Notez la présence d'une annonce dans la liste **Annonces** une fois la fonctionnalité désactivée.  
  
## Voir aussi  
 [Comment : créer un récepteur d'événements](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  