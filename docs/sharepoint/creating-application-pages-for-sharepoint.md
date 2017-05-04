---
title: "Cr&#233;ation de pages d&#39;application pour SharePoint | Microsoft Docs"
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
  - "pages d'application (développement SharePoint dans Visual Studio), créer"
  - "pages d'application (développement SharePoint dans Visual Studio), développer"
  - "développement SharePoint dans Visual Studio, pages d'application"
  - "développement SharePoint dans Visual Studio, pages de contenu"
  - "développement SharePoint dans Visual Studio, pages Web"
ms.assetid: a6e97149-15dd-4bdb-8d75-3b53f886f76c
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Cr&#233;ation de pages d&#39;application pour SharePoint
  Une *page d'application* est une page Web ASP.NET conçue pour être utilisée dans un site Web SharePoint.  Les pages d'application sont un type spécifique de page ASP.NET.  La différence entre une page d'application et une page ASP.NET standard réside essentiellement dans le fait qu'une page d'application contient du contenu qui est fusionné avec une page maître SharePoint.  Une page maître permet aux pages d'application de partager la même apparence et le même comportement que d'autres pages sur un site.  
  
 Visual Studio vous permet de concevoir des pages d'application à l'aide d'un concepteur.  Ce concepteur affiche une zone de contenu pour chaque espace réservé de contenu défini dans une page maître.  Vous pouvez concevoir la page d'application en faisant glisser des contrôles sur ces zones de contenu.  
  
## Pages d'application  
 Les pages d'application sont partagées entre tous les sites présents sur un serveur, alors qu'une page de site est spécifique à un site.  Pour plus d'informations, consultez [Types de pages SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
 Par défaut, la plupart des pages qui s'affichent lorsque vous créez un site SharePoint sont des pages de site.  Une page de site peut être ajoutée à une bibliothèque de pages SharePoint.  Les utilisateurs peuvent personnaliser une page de site à l'aide d'outils, tels que SharePoint Designer.  Une page de site peut également héberger des fonctionnalités, telles que des composants WebPart dynamiques et des zones de composants WebPart.  
  
 Les pages d'application ne fonctionnent pas de cette manière.  Une page d'application reste toutefois le meilleur type de page à créer si vous souhaitez que la page contienne du code personnalisé.  Même si vous pouvez ajouter du code personnalisé à une page de site, le code cesse de s'exécuter lorsque l'utilisateur personnalise la page à l'aide d'outils, tels que SharePoint Designer.  
  
> [!NOTE]  
>  Visual Studio ne fournit pas de modèles qui vous aident à créer des pages de site pour un site SharePoint.  Pour plus d'informations, consultez [Types de pages SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
## Création d'une page d'application  
 Pour créer une page d'application, ajoutez un élément **Page Application** à un projet SharePoint.  Lorsque vous créez une page d'application, Visual Studio ajoute les dossiers suivants à votre projet :  
  
|Dossier|Description|  
|-------------|-----------------|  
|Dispositions|Est mappé au répertoire virtuel \_layouts du système de fichiers SharePoint.|  
|Sous\-dossier Dispositions|Contient les fichiers qui composent la page d'application.  Par défaut, ce dossier porte le même nom que votre projet.  Vous pouvez renommer ce dossier à tout moment.  Lorsque vous exécutez le projet, Visual Studio déploie ce dossier dans le répertoire virtuel \_layouts du système de fichiers SharePoint.|  
  
 Visual Studio ajoute les fichiers suivants à votre projet :  
  
|Fichier|Description|  
|-------------|-----------------|  
|Fichier de page ASP.NET \(.aspx\)|Contient le balisage XML qui définit la page.|  
|Fichier de code de la page d'application|Contient le code\-behind de la page d'application.  Vous pouvez ajouter à ce fichier du code qui gère des événements.|  
|Fichier de code du concepteur de la page d'application|Contient le code qui est généré par le concepteur.  Ne modifiez pas ce fichier directement.|  
  
## Conception et débogage d'une page d'application  
 Vous pouvez concevoir le contenu d'une page d'application à l'aide du concepteur Visual Web Developer dans Visual Studio.  Ce concepteur s'affiche lorsque vous ouvrez la page de l'application dans votre projet \(en double\-cliquant dessus ou en ouvrant le menu contextuel puis en choisissant **Ouvrir**\).  Pour plus d'informations sur l'utilisation de ce concepteur, consultez [Visual Studio Web Development Content Map](http://msdn.microsoft.com/fr-fr/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
> [!NOTE]  
>  Vous pouvez uniquement concevoir la page dans le mode **Source** du concepteur.  Le mode **Design** du concepteur est désactivé pour les pages d'application.  
  
 Vous pouvez déboguer une page d'application de la même manière que vous le feriez avec d'autres éléments d'un projet SharePoint dans Visual Studio.  Lorsque vous démarrez le débogueur Visual Studio, Visual Studio ouvre le site SharePoint.  
  
 Pour afficher la page d'application, vous devez naviguer manuellement jusqu'à l'emplacement de la page d'application \(par exemple, http:\/\/*Server\_Name*\/\_layouts\/*Project\_Name*\/ApplicationPage1.aspx\).  
  
 Pour plus d'informations sur le débogage de projets SharePoint, consultez [Dépannage des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Choix d'une page maître  
 Par défaut, un élément **Page Application** référence la page maître du site que vous utilisez pour déboguer votre projet.  Cette page, nommée V4.master, figure dans la **Galerie de pages maîtres** du site SharePoint.  
  
 Vous pouvez changer explicitement la page maître qui est utilisée par la page d'application en définissant l'attribut `MasterPageFile` de l'élément `Page` de l'application. \(par exemple, `MasterPageFile="~/_layouts/applicationv4.master"`\).  Vous devez en fait définir cet attribut lorsque les pages maîtres dynamiques ne sont pas activées sur le serveur SharePoint.  Pour plus d'informations sur les pages maître dans SharePoint, consultez [Pages maître](http://go.microsoft.com/fwlink/?LinkID=169281).  
  
## Voir aussi  
 [Développement de SharePoint Foundation détaillé](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [Vue d'ensemble des pages Web ASP.NET](../Topic/ASP.NET%20Web%20Forms%20Pages%20Overview.md)   
 [Vue d'ensemble de la syntaxe des pages Web ASP.NET](../Topic/ASP.NET%20Web%20Forms%20Page%20Syntax%20Overview.md)   
 [Programmation de pages Web ASP.NET](http://msdn.microsoft.com/fr-fr/5626c661-8057-4de8-b658-c2e35ed4b4c9)  
  
  