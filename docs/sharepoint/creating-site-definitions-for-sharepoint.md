---
title: "Cr&#233;ation de d&#233;finitions de site pour SharePoint | Microsoft Docs"
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
  - "développement SharePoint dans Visual Studio, définitions de sites"
  - "définitions de sites (développement SharePoint dans Visual Studio)"
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Cr&#233;ation de d&#233;finitions de site pour SharePoint
  Le projet de définition de site SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] permet de créer une *définition de site* faisant office de base pour un nouveau site SharePoint.  Ces définitions spécifient non seulement l'aspect et le comportement du site SharePoint, mais également son contenu par défaut et son mode de fonctionnement.  Dans la définition vous pouvez placer des listes préconfigurées, des types de contenu, des récepteurs d'événements, des images, ainsi que d'autres éléments.  SharePoint inclut des définitions de site telles que BLOG, par exemple.  Lorsque vous créez un site basé sur la définition de site BLOG, le site intègre les listes, les composants WebPart et les autres éléments nécessaires à ce type de site.  
  
 Pour plus d'informations sur les définitions de site, consultez [Modèles et définitions de site](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## Projets de définition de site  
 Les projets de définition de site dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fournissent uniquement les fichiers de base dont un site SharePoint a besoin ; aucune fonctionnalité par défaut n'est prévue.  Il vous appartient d'ajouter les fichiers et le contenu correspondant aux fonctionnalités que vous souhaitez mettre en place.  Vous pouvez générer le site de façon manuelle \(en créant et ajoutant les fichiers dont vous avez besoin\),  
  
## Association de fonctions  
 Les définitions de site créées dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] offrent un avantage intéressant en ce sens qu'elles permettent de recourir automatiquement à l'*association de fonctions*.  L'association de fonctions a pour effet de joindre une fonctionnalité à une définition de site au lieu de l'incorporer à la définition de site elle\-même.  Vous avez ainsi la possibilité d'ajouter la fonctionnalité à tous les sites que vous créez en utilisant simplement la définition du site sans modifier celle d'origine.  Pour plus d'informations, consultez [Fonctionnalités d'attachement](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## Composants d'un projet de définition de site  
 La création d'une solution de définition de site a pour effet d'ajouter les fichiers par défaut suivants au nœud **SiteDefinition**.  
  
|Nom de fichier|Description|  
|--------------------|-----------------|  
|default.aspx|Page d'accueil ASPX par défaut pour le nouveau site SharePoint.|  
|onet.xml|Ensemble des paramètres définissant la configuration du nouveau site, les composants du modèle de définition de site et le comportement par défaut.  Ces paramètres peuvent comprendre des attributs tels que les types de contenu activés, les vues Liste par défaut, les fichiers modèles de documents et les composants WebPart inclus avec le site.  Par défaut, la section `Modules` répertorie les fichiers à ajouter au site SharePoint et décrit leur mode de configuration.|  
|webtemp\_*SiteDefinitionName*.xml|Spécifie les configurations de définition de site qui s'affichent dans la section **Sélection du modèle** de la page **Nouveau site SharePoint**.|  
  
 Par défaut, toutes les définitions de site sont stockées dans le dossier *drive:*\\Program Files\\Fichiers communs\\Microsoft Shared\\Web Server Extensions\\14\\TEMPLATE\\SiteTemplates.  Chaque définition de site possède son propre sous\-dossier.  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Procédure pas à pas : création d'un projet de définition de site de base](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Vous guide pas à pas dans la création d'un projet de définition de site de base dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Comment : Créer une définition de site et une configuration personnalisées](http://go.microsoft.com/fwlink/?LinkId=183309)|Explique comment créer une définition de site personnalisée dans SharePoint en copiant une définition de site existante, puis en modifiant la copie.|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|Décrit le fichier d'origine qui spécifie les définitions de site disponibles dans la section **Sélection du modèle** de la page **Nouveau site SharePoint**.|  
|[Localisation de solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Explique comment préparer vos solutions SharePoint pour une utilisation globale.|  
|[Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Explique comment concevoir des parties d'une page SharePoint modifiables par les utilisateurs.|  
|[Création de contrôles réutilisables pour les composants WebPart ou les pages d'application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Explique comment créer des contrôles réutilisables prévus pour s'exécuter dans les pages d'applications et les composants WebPart.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Explique comment utiliser le concepteur qui s'affiche lorsque vous ouvrez une page Web dans votre projet.|  
|[Vue d'ensemble des pages Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Informations générales à propos de la structure des pages Web [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], du mode de traitement des pages par [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] et du mode d'affichage du balisage conforme aux normes XHTML dans les pages [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)].|  
|[ASP.NET Web Page Syntax](http://go.microsoft.com/fwlink/?LinkId=178727)|Description des éléments de balisage qui composent une page ASP.NET.|  
|[Programmation de pages Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178728)|Informations sur la méthode de création des gestionnaires d'événements dans les pages [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] et sur le mode d'emploi d'un script client.|  
|[Programmation dans Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Explique comment utiliser le modèle d'objet managé fourni dans [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## Voir aussi  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  