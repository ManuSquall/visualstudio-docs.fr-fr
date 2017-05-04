---
title: "Comment&#160;: ajouter un descripteur de filtre &#224; une m&#233;thode de recherche | Microsoft Docs"
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
  - "BDC (développement SharePoint dans Visual Studio), ajouter un filtre"
  - "BDC (développement SharePoint dans Visual Studio), descripteurs de filtre"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), ajouter un filtre"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), descripteurs de filtre"
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: ajouter un descripteur de filtre &#224; une m&#233;thode de recherche
  Les descripteurs de filtre permettent aux consommateurs du modèle de passer des valeurs aux méthodes avant leur exécution.  Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Il arrive fréquemment que les utilisateurs dans SharePoint souhaitent extraire des instances d'un type de contenu externe qui correspondent à certains critères.  Vous pouvez prendre en charge ce scénario en ajoutant un descripteur de filtre à une méthode de recherche.  
  
### Pour ajouter un descripteur de filtre à une méthode de recherche  
  
1.  Dans la fenêtre **Détails de méthode BDC**, développez le nœud d'une méthode de recherche, développez le nœud **Paramètres**, puis ajoutez un paramètre d'entrée.  Pour plus d'informations, consultez [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  Dans la fenêtre **Détails de méthode**, choisissez le descripteur de type du paramètre.  
  
3.  Dans la barre de menus, choisissez **Affichage**, **Fenêtre Propriétés**.  
  
4.  Dans la fenêtre **Propriétés**, affectez à la propriété **Type Name** un type de données approprié pour le filtre.  
  
     Par exemple, un filtre peut utiliser une date de commande pour limiter le nombre de commandes client retournées par la méthode.  Pour prendre en charge ce filtre, la propriété **Type Name** du descripteur de type doit avoir la valeur **System.DateTime**.  
  
5.  Dans la fenêtre **Détails de méthode**, développez le nœud **Descripteurs de filtre**.  
  
6.  Dans la liste **Ajouter un descripteur de filtre**, choisissez **Créer un descripteur de filtre**.  
  
     Un nouveau descripteur de filtre apparaît sous le nœud **Descripteurs de filtre**.  
  
7.  Dans la barre de menus, choisissez **Affichage**, **Fenêtre Propriétés**.  
  
8.  Dans la fenêtre **Propriétés**, choisissez la propriété **Type**.  
  
9. Dans la liste qui apparaît pour la propriété **Type**, choisissez le modèle de filtrage de votre choix.  
  
     Par exemple, pour créer un filtre qui utilise une date de commande pour limiter le nombre de commandes client retournées dans une méthode de recherche, choisissez **Comparaison**.  Un filtre de comparaison garantit qu'une méthode de détecteur retourne uniquement les instances qui répondent à une condition spécifique.  Pour plus d'informations sur chaque modèle de filtrage, consultez [Types de filtres pris en charge par le BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. Dans la fenêtre **Propriétés**, choisissez la propriété **Associated Type Descriptors**.  
  
11. Dans la liste qui apparaît pour la propriété **Associated Type Descriptors**, choisissez le descripteur de type que vous avez créé précédemment dans cette procédure.  Cela lie le filtre au paramètre d'entrée de la méthode de recherche.  
  
12. Ajoutez du code à la méthode de recherche qui retourne des données.  Vous pouvez utiliser le paramètre d'entrée comme condition dans une requête Select.  
  
     L'exemple suivant retourne les commandes client avec la date de commande spécifiée.  
  
    > [!NOTE]  
    >  Remplacez la valeur du champ `ServerName` par le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#11](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#11)]  
  
## Voir aussi  
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  