---
title: "Comment&#160;: cr&#233;er un r&#233;cepteur d&#39;&#233;v&#233;nements pour une instance de liste sp&#233;cifique | Microsoft Docs"
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
helpviewer_keywords: 
  - "récepteurs d'événements (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, récepteurs d'événements"
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Comment&#160;: cr&#233;er un r&#233;cepteur d&#39;&#233;v&#233;nements pour une instance de liste sp&#233;cifique
  Un récepteur d'événements d'instance de liste répond aux événements qui se produisent dans une instance de définition de liste.  Bien que le modèle de récepteur d'événements ne permette pas de cibler une instance de liste spécifique, vous pouvez modifier un récepteur d'événements limité à une définition de liste pour répondre aux événements qui se produisent dans une instance de liste spécifique.  
  
 Pour cibler une instance de liste spécifique, dans le fichier Elements.xml du récepteur d'événements, remplacez `ListTemplateId` par `ListUrl` et ajoutez l'URL de l'instance de liste.  
  
## Création d'un récepteur d'événements d'instance de liste  
 Les étapes suivantes indiquent comment modifier un récepteur d'événements d'élément de liste pour qu'il réponde uniquement aux événements qui se produisent dans une instance de liste d'annonce personnalisée.  
  
#### Pour modifier un récepteur d'événements pour qu'il réponde à une instance de liste spécifique  
  
1.  Dans un navigateur, ouvrez le site SharePoint .  
  
2.  Dans le volet de navigation, lien **Listes**.  
  
3.  Dans la page **Tout le contenu du site**, sélectionnez le lien **Créer**.  
  
4.  Dans la boîte de dialogue **Créer**, choisissez le type **Annonces**, attribuez le nom TestAnnouncements à l'annonce, et choisissez me bouton **Créer**.  
  
5.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet de récepteur d'événements.  
  
6.  Dans la liste **Quel type de récepteur d'événements voulez\-vous**, choisissez **Liste des événements d'élément**.  
  
    > [!NOTE]  
    >  Vous pouvez également sélectionner un autre type de récepteur d'événements limité à une définition de liste, par exemple **Liste des événements de courrier électronique** ou **Liste des événements de flux de travail**.  
  
7.  Dans la liste **Quel élément doit être la source d'événements ?**, choisissez **Annonces**.  
  
8.  Dans la liste **Gérer les événements suivants**, sélectionner la case **Un élément est en cours d'ajout**, puis cliquez sur le bouton **Terminer**.  
  
9. Dans l'**Explorateur de solutions**, sous EventReceiver1, ouvrez le fichier Elements.xml.  
  
     Le récepteur d'événements fait actuellement référence à la définition de liste Annonces dans la ligne suivante :  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     Modifiez cette ligne du texte suivant :  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     Cette opération indique au récepteur d'événements qu'il doit répondre uniquement aux événements qui se produisent dans la nouvelle liste d'annonces **TestAnnouncements** que vous venez de créer.  Vous pouvez modifier l'attribut `ListURL` pour référencer n'importe quelle instance de liste sur le serveur SharePoint.  
  
10. Ouvrez le fichier de code du récepteur d'événements et placez un point d'arrêt dans la méthode ItemAdding.  
  
11. Appuyez sur la touche F5 pour générer et exécuter la solution.  
  
12. Dans SharePoint, dans le volet de navigation, choisissez **TestAnnouncements**.  
  
13. Choisissez le lien **Ajouter une nouvelle annonce**.  
  
14. Entrez un titre pour l'annonce, puis cliquez sur le bouton **Enregistrer**.  
  
     Notez que le point d'arrêt est atteint lorsque le nouvel élément est ajouté à la liste d'annonce personnalisée.  
  
15. Choisissez la touche F5 pour continuer.  
  
16. Dans le volet de navigation, cliquez sur le lien **Listes**, puis cliquez sur le lien **Annonces**.  
  
17. Ajoutez une annonce.  
  
     Notez que le récepteur d'événements ne se déclenche pas pour la nouvelle annonce car il est configuré pour répondre uniquement aux événements qui se produisent dans l'instance de liste d'annonce personnalisée, **TestAnnouncements**.  
  
## Voir aussi  
 [Comment : créer un récepteur d'événements](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  