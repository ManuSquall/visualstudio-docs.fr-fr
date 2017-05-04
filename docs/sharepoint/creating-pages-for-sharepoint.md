---
title: "Cr&#233;ation de pages pour SharePoint | Microsoft Docs"
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
  - "pages de contenu (développement SharePoint dans Visual Studio), concevoir"
  - "pages maîtres (développement SharePoint dans Visual Studio), concevoir"
  - "mises en page (développement SharePoint dans Visual Studio), concevoir"
  - "développement SharePoint dans Visual Studio, pages de contenu"
  - "développement SharePoint dans Visual Studio, pages maîtres"
  - "développement SharePoint dans Visual Studio, mises en page"
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Cr&#233;ation de pages pour SharePoint
  Vous pouvez créer des pages d'application, des pages de site, des pages maîtres et des mises en page pour un site SharePoint.  
  
 Vous pouvez créer des pages d'application à l'aide d'un modèle dans Visual Studio.  Créez des pages de contenu, des pages maîtres et des mises en page à l'aide de SharePoint Designer.  Vous pouvez ensuite importer ces pages dans Visual Studio pour les utiliser dans un projet SharePoint.  
  
 Vous pouvez également modifier l'apparence et le comportement des pages à l'aide de feuilles de style en cascade, de scripts ECMAScript et de thèmes.  
  
## Types de pages SharePoint  
 Le tableau suivant décrit les quatre types principaux de pages figurant dans un site SharePoint.  
  
|Type de page|Description|  
|------------------|-----------------|  
|Pages d'application|Créez une page d'application si vous souhaitez que la page contienne du code personnalisé ou qu'elle soit partagée par plusieurs sites.  Sinon, une page de site peut représenter le choix le plus approprié.|  
|Pages de site|Créez une page de site si vous souhaitez exécuter l'une des tâches suivantes :<br /><br /> -   Ajouter la page à une bibliothèque SharePoint.<br />-   Héberger dans la page des fonctionnalités, telles que des composants WebPart dynamiques et des zones de composants WebPart.<br />-   Permettre aux utilisateurs de personnaliser la page à l'aide de SharePoint Designer.<br /><br /> Ne créez pas de page de site si vous souhaitez que la page contienne du code personnalisé.  Bien que vous puissiez ajouter du code personnalisé à une page de site, le code cesse de s'exécuter lorsque l'utilisateur personnalise la page à l'aide de SharePoint Designer.|  
|Pages maîtres|Créez une page maître si vous souhaitez définir une structure commune pour les pages de site et les pages d'application.|  
|Mises en page|Les mises en page sont spécifiques à [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] et vous permettent de définir plus précisément une structure commune pour les pages de site et les pages d'application.|  
  
 Pour obtenir une vue d'ensemble de chaque type de page, consultez [Bloc de construction : Pages et l'interface utilisateur](http://go.microsoft.com/fwlink/?LinkID=182095), et [Mises en page et pages maîtres](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## Création de pages d'application  
 Vous pouvez créer des pages d'application dans Visual Studio en ajoutant un élément **Page Application** à un projet SharePoint.  Vous avez la possibilité d'ajouter des contrôles à la page, puis de gérer les événements de contrôle en ajoutant du code.  
  
 Vous pouvez définir des points d'arrêt dans le fichier de code de la page, démarrer le débogueur et tester la page sur un site SharePoint local sans exécuter d'autres opérations de configuration.  Pour plus d'informations, consultez [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## Création de pages de site, de pages maîtres et de mises en page  
 Vous avez la possibilité de créer des pages de site, des pages maîtres et des mises en page à l'aide de SharePoint Designer.  Vous pouvez ensuite importer ces pages dans Visual Studio.  Importez vos pages si vous souhaitez tirer parti des fonctionnalités de déploiement ou de contrôle de code source qui sont disponibles dans Visual Studio.  Pour plus d'informations, consultez [Importation d'éléments d'un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Étant donné qu'il est difficile de modifier ces pages une fois qu'elles ont été importées, vous devez les concevoir avant de les importer.  
  
## Création de feuilles de style en cascade, de scripts ECMAScript et de thèmes  
 Visual Studio ne fournit pas de modèles pour le développement des feuilles de style en cascade \(CSS\), des scripts ECMAScript \(JavaScript et JScript\), ou des fichiers de thème qui sont destinés aux sites SharePoint.  Vous pouvez créer ces fichiers en suivant les indications du Kit de développement logiciel \(SDK\) SharePoint ou en utilisant des outils tels que SharePoint Designer.  
  
 Vous avez la possibilité d'ajouter directement ces fichiers à votre solution ou de les importer.  Dans les deux cas, vous devez créer les dossiers mappés appropriés pour chaque élément que vous ajoutez.  Pour plus d'informations sur la création d'un dossier mappé, consultez [Comment : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Pour plus d'informations sur la création de feuilles de style en cascade, consultez [Utilisation des classes de feuilles de style en cascade dans SharePoint Foundation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=182098).  Pour plus d'informations sur la création de fichiers JavaScript et JScript pour une solution SharePoint, consultez [Configuration d'une page ASPX de base pour ECMAScript \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=182099).  Pour plus d'informations sur les produits mentionnés, consultez [Bloc de construction : Pages et l'interface utilisateur](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Explique comment ajouter des pages applications : contenu .aspx fusionné avec une page maître SharePoint.|  
|[Comment : créer une page d'application](../sharepoint/how-to-create-an-application-page.md)|Indique comment créer des pages ASP.NET qui s'exécutent sur un site SharePoint.|  
|[Procédure pas à pas : création d'une page d'application SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Vous indique comment concevoir et déboguer une page Web ASP.NET pour un site SharePoint.|  
|[Utilisation de Visual Web Developer](http://msdn.microsoft.com/fr-fr/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Explique comment utiliser le concepteur qui s'affiche lorsque vous ouvrez une page Web dans votre projet.|  
  
  