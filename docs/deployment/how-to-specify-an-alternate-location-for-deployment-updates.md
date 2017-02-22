---
title: "How to: Specify an Alternate Location for Deployment Updates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, updates"
  - "deployment update, alternative locations"
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Specify an Alternate Location for Deployment Updates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez procéder à la toute première installation de votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à partir d'un CD ou d'un partage de fichiers, mais l'application doit rechercher des mises à jour périodiques sur le Web.  Vous pouvez spécifier un autre emplacement pour les mises à jour dans votre manifeste de déploiement afin que votre application puisse se mettre à jour à partir du Web après son installation initiale.  
  
> [!NOTE]
>  Votre application doit être configurée pour une installation locale afin d'utiliser cette fonctionnalité.  Pour plus d'informations, consultez [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  De plus, si vous installez une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à partir du réseau et que vous définissez un autre emplacement, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilise cet emplacement à la fois pour l'installation initiale et toutes les mises à jour ultérieures.  Si vous installez votre application localement \(par exemple, à partir d'un CD\), l'installation initiale est réalisée avec le média d'origine et toutes les mises à jour ultérieures utiliseront l'autre emplacement.  
  
### Spécification d'un autre emplacement pour les mises à jour avec MageUI.exe \(utilitaire Windows Forms\)  
  
1.  Ouvrez une invite de commandes du .NET Framework et tapez :  
  
     **mageui.exe**  
  
2.  Dans le menu **File**, choisissez **Open** pour ouvrir le manifeste de déploiement de votre application.  
  
3.  Sélectionnez l'onglet **Deployment Options**.  
  
4.  Dans la zone de texte **Launch Location**, entrez l'URL vers le répertoire qui doit contenir le manifeste de déploiement pour les mises à jour d'application.  
  
5.  Enregistrez le manifeste de déploiement.  
  
### Spécification d'un autre emplacement pour les mises à jour avec Mage.exe  
  
1.  Ouvrez une invite de commandes du .NET Framework.  
  
2.  Définissez l'emplacement de mise à jour à l'aide de la commande suivante.  Dans cet exemple, **HelloWorld.exe.application** est le chemin d'accès à votre manifeste d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], toujours affecté de l'extension .application et **http:\/\/adatum.com\/Update\/Path** est l'URL que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vérifie pour les mises à jour de l'application.  
  
     **Mage \-Update HelloWorld.exe.application \-ProviderUrl http:\/\/adatum.com\/Update\/Path**  
  
3.  Enregistrez le fichier.  
  
    > [!NOTE]
    >  Vous devez maintenant signer à nouveau le fichier avec Mage.exe.  Pour plus d'informations, consultez [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Sécurité .NET Framework  
 Si vous installez votre application à partir d'un support hors connexion tel qu'un CD et que l'ordinateur est en ligne, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vérifie d'abord l'URL spécifiée par la balise `<deploymentProvider>` dans le manifeste de déploiement afin de déterminer si l'emplacement de mise à jour contient une version plus récente de l'application.  Si c'est le cas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installe directement l'application à partir de cet emplacement au lieu du répertoire d'installation initial et le Common Language Runtime \(CLR\) détermine le niveau de confiance de votre application à l'aide de `<deploymentProvider>`.  Si l'ordinateur est hors connexion ou si `<deploymentProvider>` est inaccessible, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] s'installe à partir du CD, et le CLR accorde un niveau de confiance en fonction du point d'installation ; dans le cas d'une installation à partir d'un CD, votre application obtient un niveau de confiance totale.  Toutes les mises à jour ultérieures hériteront du même niveau de confiance.  
  
 Toutes les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui utilisent `<deploymentProvider>` doivent déclarer explicitement les autorisations dont elles ont besoin dans leur manifeste d'application, afin que l'application ne bénéficie pas de niveaux de confiance différents sur divers ordinateurs.  
  
## Voir aussi  
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)