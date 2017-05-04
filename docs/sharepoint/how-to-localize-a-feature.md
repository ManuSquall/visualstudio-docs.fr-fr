---
title: "Comment&#160;: localiser une fonctionnalit&#233; | Microsoft Docs"
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
  - "fonctionnalités (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, localiser"
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Comment&#160;: localiser une fonctionnalit&#233;
  Par défaut, les titres et les descriptions des fonctionnalités utilisent des valeurs de chaîne codées en dur.  Pour localiser le titre et la description d'une fonctionnalité, remplacez les chaînes par des expressions qui référencent des ressources localisées.  
  
## Localisation d'une fonctionnalité  
  
#### Pour localiser une fonctionnalité  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du nœud **Feature1**, puis choisissez **Ajouter une ressource de composant**.  
  
2.  Dans la boîte de dialogue **Ajouter une ressource**, choisissez **Langue invariante** dans la liste comme culture du fichier des ressources de composants de langue par défaut.  
  
3.  Répétez l'étape précédente pour chaque langue localisée, en choisissant les langues de votre choix pour les fichiers de ressources de fonctionnalité localisés.  
  
     Des fichiers séparés de ressources de fonctionnalité sont créés : un pour la langue par défaut et un pour chaque langue localisée que vous souhaitez prendre en charge.  
  
4.  Ouvrez chaque fichier de ressources dans l'Éditeur de ressources, puis entrez tous les IDs de chaînes et leurs valeurs.  
  
     Par exemple, dans le fichier de ressources de fonctionnalité par défaut, entrez un ID de chaîne Titre avec la valeur Mon titre de fonctionnalité, et un deuxième ID de chaîne Description avec la valeur Ma description de la fonctionnalité.  Pour chaque fichier de ressources localisé, utilisez le même ID de chaîne que celui utilisé dans la ressource de fonctionnalité par défaut, mais entrez des chaînes localisées pour les valeurs.  
  
5.  Après avoir entré toutes les valeurs de ressources, ouvrez le menu contextuel de la fonction \(par exemple, Feature1.feature\), puis choisissez **Concepteur de vues** pour ouvrir les fonctionnalités du concepteur de fonctionnalité.  
  
6.  Pour localiser les champs **Titre** et **Description** dans la fonctionnalité, utilisez le format suivant pour entrer des valeurs dans leur zones :  
  
     `$Resources:` *String ID*  
  
     Par exemple, entrez $Resources:Title dans la zone **Titre de la fonctionnalité** et $Resources:Description dans la zone **Description de la fonctionnalité**.  
  
     L'IDs de chaîne doit correspondre à ceux utilisés dans les fichiers de ressources.  
  
7.  Appuyez sur la touche F5 pour générer et exécuter l'application.  
  
8.  Dans SharePoint, ouvrez le menu **Actions du site**, choisissez**Paramètre du site**, puis dans la section **Actions du site**, cliquez sur le lien **Gérer les fonctionnalités du site**.  
  
9. Dans SharePoint, modifiez la langue d'affichage par défaut.  
  
     Le titre et la description de la fonctionnalité localisée s'affichent dans l'application.  Pour afficher les ressources localisées, un module linguistique qui correspond à la culture du fichier de ressources doit être installé sur le serveur SharePoint.  
  
## Voir aussi  
 [Localisation de solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)   
 [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Comment : localiser du code](../sharepoint/how-to-localize-code.md)  
  
  