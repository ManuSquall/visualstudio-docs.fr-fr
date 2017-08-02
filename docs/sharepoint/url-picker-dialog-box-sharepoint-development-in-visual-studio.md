---
title: "Bo&#238;te de dialogue du s&#233;lecteur d&#39;URL (d&#233;veloppement SharePoint dans Visual Studio)"
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
  - "VS.SharePointTools.VWD.URLPicker"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, concepteur"
  - "développement SharePoint dans Visual Studio, sélecteur d'URL"
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Bo&#238;te de dialogue du s&#233;lecteur d&#39;URL (d&#233;veloppement SharePoint dans Visual Studio)
  Dans la boîte de dialogue du sélecteur d'URL, vous avez la possibilité de choisir des fichiers tels que des fichiers de page maître ou des fichiers image se trouvant dans votre projet ou sur le serveur qui exécute SharePoint.  
  
 Cette boîte de dialogue apparaît lorsque vous avez la possibilité de choisir un fichier pour définir une propriété.  Vous pouvez ouvrir cette boîte de dialogue en choisissant le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](~/sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile") \) en regard de différentes propriétés dans la fenêtre **Propriétés**.  Le bouton de sélection apparaît également comme une invite IntelliSense lorsque vous assignez des valeurs à certains attributs à partir du mode **Source** du concepteur.  
  
## Liste UIElement  
 **Dossiers du projet**  
 Affiche la liste des dossiers définis dans le projet ou sur le serveur qui exécute SharePoint.  Choisissez le bouton de développement pour afficher les sous\-dossiers.  
  
 Développez le nœud **Projet** pour choisissez des fichiers dans votre projet.  Pour apparaître comme sélectionnables dans la boîte de dialogue, les fichiers dans votre projet doivent être conformes aux critères suivants :  
  
-   Le fichier doit se trouver dans un dossier mappé.  
  
-   Le fichier doit être ajouté au package de solution.  
  
-   Le fichier ne peut pas figurer dans un autre projet.  
  
 Si vous souhaitez référencer des fichiers non conformes à ces critères, vous devez entrer manuellement le chemin d'accès du fichier.  
  
 Développez le nœud **Serveur** pour choisir les fichiers situés sur le serveur local exécutant SharePoint.  Pour apparaître comme sélectionnables dans la boîte de dialogue, ces fichiers doivent être conformes aux critères suivants :  
  
-   Le fichier doit se trouver dans l'un des dossiers mappés suivants : **Images**, **Layouts** ou **ControlTemplates**.  
  
-   Le fichier ne peut pas se trouver dans la base de données de contenu SharePoint.  
  
 Si vous souhaitez référencer des fichiers non conformes à ces critères, vous devez entrer manuellement le chemin d'accès du fichier.  
  
 **Contenu du dossier**  
 Affiche la liste des fichiers du dossier sélectionné.  Choisissez un fichier, puis choisissez le bouton **OK** pour fermer la boîte de dialogue et envoyer votre sélection au processus qui l'a appelée.  
  
 **Type de fichiers**  
 Vous permet de choisir dans une liste de fichiers appropriés à la tâche que vous exécutez.  
  
## Voir aussi  
 [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Création de contrôles réutilisables pour les composants WebPart ou les pages d'application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/fr-fr/9c31f93b-c8fb-4599-9b14-6194ec8c7539)  
  
  