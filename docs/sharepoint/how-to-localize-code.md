---
title: "Comment&#160;: localiser du code"
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
  - "localiser le code (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, localiser"
ms.assetid: 0e852052-5ad4-4517-81cf-8865ec304441
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Comment&#160;: localiser du code
  Le code non localisé utilise des valeurs de chaîne codées en dur.  Pour localiser des chaînes de code, remplacez\-les par des appels à <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, qui est une méthode référençant les ressources localisées.  
  
## Localisation du code  
  
#### Pour localiser le code  
  
1.  Dans **l'Explorateur de solutions**, ouvrez le menu contextuel d'un élément du projet, puis choisissez **Ajouter**, **Module**.  
  
     Sélectionnez le modèle **Fichier de ressources**.  
  
    > [!NOTE]  
    >  Veillez à ajouter le fichier de ressources à un élément de projet SharePoint afin que la propriété Deployment Type soit disponible.  Cette propriété est requise plus loin dans cette procédure.  
  
2.  Attribuez au fichier de ressources de langue par défaut le nom de votre choix, avec l'extension .resx, par exemple MyAppResources.resx.  
  
3.  Répétez les étapes 1 et 2 pour ajouter des fichiers ressources séparés à l'élément du projet SharePoint : un pour chaque langue locale.  
  
     Utilisez le même nom de base pour chaque fichier de ressources localisé, en y ajoutant l'ID de culture.  Par exemple, nommez une ressource localisée en allemand MyAppResources.de\-DE.resx.  
  
4.  Ouvrez chaque fichier de ressources et ajoutez les chaînes localisées.  Utilisez les mêmes IDs de chaîne dans chaque fichier.  
  
5.  Remplacez la valeur de la propriété **Deployment Type** de chaque fichier de ressources par **AppGlobalResource** pour que chaque fichier soit déployé vers le dossier App\_GlobalResources du serveur.  
  
6.  La valeur de la propriété **Build Action** de chaque fichier doit conserver la valeur **Ressource incorporée**.  
  
     Les ressources incorporées sont compilées dans la DLL du projet.  
  
7.  Générez le projet pour créer les DLL satellites de ressources.  
  
8.  Dans le **Concepteur de packages**, cliquez sur l'onglet **Avancé** , puis ajoutez l'assembly satellite.  
  
9. Dans la boite **Emplacement**, ajoutez avant un dossier de culture ID dans le chemin d'accès, par exemple de\-DE\\*Project Item Name*.resources.dll.  
  
10. Si votre solution ne référence pas déjà l'assembly System.Web, ajoutez une référence à celui\-ci et ajoutez une directive dans votre code pour <xref:System.Web>.  
  
11. Recherchez toutes les chaînes codées en dur dans votre code qui sont visibles par les utilisateurs, tels que le texte d'interface utilisateur, les erreurs, et le texte du message.  Remplacez\-les par un appel à la méthode <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> en utilisant la syntaxe suivante :  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Appuyez sur la touche F5 pour générer et exécuter l'application.  
  
13. Dans SharePoint, modifiez la langue d'affichage par défaut.  
  
     Les chaînes localisées s'affichent dans l'application.  Pour afficher les ressources localisées, un module linguistique qui correspond à la culture du fichier de ressources doit être installé sur le serveur SharePoint.  
  
## Voir aussi  
 [Localisation de solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)   
 [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)  
  
  