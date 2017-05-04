---
title: "S&#233;curit&#233; pour les solutions SharePoint | Microsoft Docs"
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
  - "sécurité (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, sécurité"
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# S&#233;curit&#233; pour les solutions SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] intègre les fonctionnalités suivantes pour améliorer la sécurité des applications SharePoint.  
  
## Entrées de contrôle sécurisé  
 Chaque élément de projet SharePoint créé dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a une propriété **Entrées de contrôle sécurisé** qui représente une collection de contrôles sécurisés.  Sa sous\-propriété **Sécurisé** vous permet de spécifier les contrôles que vous considérez comme sécurisés.  Pour plus d'informations, consultez [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) et [Spécifier les composants webpart sécurisés](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## Attribut AllowPartiallyTrustedCallers  
 Par défaut, seules les applications qui reçoivent la confiance totale du système de sécurité d'accès du code du runtime peuvent accéder à un assembly de code managé partagé.  Le marquage d'un assembly doté d'une confiance totale avec l'attribut AllowPartiallyTrustedCallers permet aux assemblys dotés d'une confiance partielle d'y accéder.  
  
 L'attribut AllowPartiallyTrustedCallers est ajouté à toute solution SharePoint qui n'est pas déployée sur le Global Assembly Cache du système \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\).  Cela inclut les solutions bac à sable \(sandbox\) ou les solutions déployées sur le répertoire bin de l'application SharePoint.  Pour plus d'informations, consultez [Modifications apportées à la sécurité de la version 1 de Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) et [Déploiement de Webpart dans SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## Propriété Protégé contre les scripts  
 L'*injection de script* est l'insertion de code potentiellement nuisible dans des contrôles ou des pages Web.  Pour favoriser la protection des sites SharePoint 2010 contre l'injection de script, les collaborateurs ne peuvent pas, par défaut, afficher ou modifier des composants WebPart ou leurs propriétés.  Ce comportement est contrôlé par un attribut SafeControl appelé SafeAgainstScript.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], définissez cet attribut dans la sous\-propriété **Protégé contre les scripts** de **Entrées de contrôle sécurisé** d'un élément de projet .  Pour plus d’informations, consultez [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) et [Comment : marquer des contrôles comme étant des contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## Contrôle de compte d'utilisateur Vista et Windows 7  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] et [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] intègrent une fonction de sécurité appelée Contrôle de compte d'utilisateur \(ou UAC, User Account Control\).  Pour développer des solutions SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sur des systèmes [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] et [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], le contrôle de compte d'utilisateur requiert que vous exécutiez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en tant qu'administrateur système.  Depuis le menu **Démarrer**, ouvrez le menu contextuel du [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], puis sélectionnez **Exécuter en tant qu’administrateur**.  
  
 Pour configurer le raccourci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour toujours fonctionner en tant qu'administrateur, ouvrez son menu contextuel, sélectionnez **Propriétés**, choisissez le bouton **Avancé** dans la boîte de dialogue **Propriétés**, puis sélectionnez ensuite la case **Exécuter en tant qu’administrateur**.  
  
 Pour plus d'informations, consultez [Présentation et configuration du contrôle de compte d'utilisateur dans Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476) et [Windows 7 User Account Control](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## Considérations au sujet des autorisations SharePoint  
 Pour développer des solutions SharePoint, il est indispensable de posséder les autorisations nécessaires à leur exécution et à leur débogage.  Avant d'entreprendre le test d'une solution SharePoint, procédez comme suit pour vérifier si vous disposez des autorisations suffisantes :  
  
1.  Ajoutez votre compte d'utilisateur en tant qu'Administrateur sur le système.  
  
2.  Ajoutez votre compte d'utilisateur en tant qu'administrateur de batterie pour le serveur SharePoint.  
  
    1.  Dans l'Administration centrale de SharePoint 2010, cliquez sur le lien **Gérer le groupe Administrateurs de la batterie**.  
  
    2.  Dans la page **Gérer les administrateurs**, choisissez l'option **Nouveau** du menu  
  
3.  Ajoutez votre compte d'utilisateur au groupe WSS\_ADMIN\_WPG.  
  
## Ressources de sécurité supplémentaires  
 Pour plus d'informations sur les problèmes de sécurité, consultez les documentations suivantes.  
  
### Sécurité Visual Studio  
  
-   [Sécurité et autorisations de l'utilisateur](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Sécurité dans le code natif et .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Sécurité dans le .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### Sécurité SharePoint  
  
-   [Administration et sécurité de SharePoint foundation](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [Centre de ressources de sécurité SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Webpart de sécurisation dans SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Améliorer la sécurité pour les applications Web : Menaces et contre\-mesures](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### Sécurité générale  
  
-   [Cycle de vie de la sécurité MSDN \- Security Development Lifecycle](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Créer des applications ASP. NET sécurisées : Authentification, Autorisation, et Communication Sécurisée](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## Voir aussi  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  