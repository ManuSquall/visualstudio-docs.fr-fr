---
title: "Comment&#160;: cr&#233;er un r&#233;cepteur d&#39;&#233;v&#233;nements | Microsoft Docs"
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
  - "VS.SharePointTools.SPE.EventReceiver"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "récepteurs d'événements (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, récepteurs d'événements"
ms.assetid: 6f90cb48-eb8f-43c2-a3f7-ed4ce81aedf2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment&#160;: cr&#233;er un r&#233;cepteur d&#39;&#233;v&#233;nements
  En créant des *récepteurs d'événements*, vous pouvez répondre lorsqu'un utilisateur interagit avec les éléments SharePoint comme des listes ou des éléments de liste.  Par exemple, le code à l'intérieur du récepteur d'événements peut être déclenché quand un utilisateur modifie une entrée du calendrier ou supprime d'un nom dans une liste de contacts.  En suivant cette rubrique, vous pouvez apprendre à ajouter un récepteur d'événements à une instance de liste.  
  
 Pour effectuer ces étapes, vous devez avoir installé [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et les éditions prises en charge de Windows et SharePoint.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  Étant donné que cet exemple nécessite un projet SharePoint, vous devez également avoir effectué la procédure dans la rubrique [Procédure pas à pas : création d'une colonne de site, d'un type de contenu et d'une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
## Ajout d'un récepteur d'événements  
 Le projet que vous avez créé dans [Procédure pas à pas : création d'une colonne de site, d'un type de contenu et d'une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) inclut des colonnes personnalisées de site, une liste personnalisée, et un type de contenu.  Dans la procédure suivante, vous allez développer ce projet en ajoutant un gestionnaire d'événements simple \(récepteur d'événements\) à une instance de liste pour montrer comment gérer les événements qui se produisent dans les éléments de SharePoint tels que des listes.  
  
#### Pour ajouter un récepteur d'événements à l'instance de liste  
  
1.  Ouvrez le projet que vous avez créé dans [Procédure pas à pas : création d'une colonne de site, d'un type de contenu et d'une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
2.  Dans l'**Explorateur de solutions**, sélectionnez le nœud du projet SharePoint nommé **Clinique**.  
  
3.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
4.  Sous **Visual C\#** ou **Visual Basic**, développez le nœud **SharePoint** puis choisissez l'élément **2010**.  
  
5.  Dans le volet de **Modèles**, choisissez **Récepteur d'événements**, nommez\-le TestEventReceiver1, puis cliquez sur le bouton **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
6.  Dans la liste **Quel type de récepteur d'événements voulez\-vous**, choisissez **Liste des événements d'élément**.  
  
7.  Dans la liste **Quel élément doit être la source d'événement ?**, choisissez **Patients \(clinique\\patients\)**.  
  
8.  Dans la liste **gérer les événements suivants**, sélectionner la case à cocher en face de l'option **Un élément a été ajouté**, puis cliquez sur le bouton **Terminer**.  
  
     Le fichier de code pour le récepteur de nouvelévénement contient une méthode unique nommée `ItemAdded`.  Dans l'étape suivante, vous allez ajouter du code à la méthode afin que chaque contact soit nommé Scott Brown par défaut.  
  
9. Remplacez la méthode `ItemAdded` existante par le code suivant, et ensuite appuyez sur la touche F5 :  
  
     [!code-csharp[SP_EventReceiver#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_eventreceiver/CS/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_eventreceiver/VB/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     Le code s'exécute et le site SharePoint apparaît dans le navigateur Web.  
  
10. Dans la barre de DémarrageRapide, sélectionnez le lien **Patients**, puis sélectionnez le lien **Ajouter un nouvel élément**.  
  
     Le formulaire d'entrée pour de nouveaux éléments s'ouvre.  
  
11. Tapez les données dans les champs, puis cliquez sur le bouton **Enregistrer**.  
  
     Après avoir cliqué sur le bouton **Enregistrer**, la colonne **Nom patient** se met automatiquement à jour au nom Scott Brown.  
  
## Voir aussi  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  