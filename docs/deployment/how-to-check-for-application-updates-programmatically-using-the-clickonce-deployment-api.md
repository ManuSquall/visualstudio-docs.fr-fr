---
title: "How to: Check for Application Updates Programmatically Using the ClickOnce Deployment API | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "application updates"
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Check for Application Updates Programmatically Using the ClickOnce Deployment API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce offre deux méthodes de mise à jour d'une application après son déploiement.  La première méthode consiste à configurer le déploiement ClickOnce pour vérifier automatiquement les mises à jour à certains intervalles.  La seconde méthode consiste à écrire du code qui utilise la classe <xref:System.Deployment.Application.ApplicationDeployment> pour vérifier les mises à jour basées sur un événement, tel qu'une demande d'utilisateur.  
  
 Les procédures suivantes affichent du code pour effectuer une mise à jour programmatique et indiquent également comment configurer votre déploiement ClickOnce pour activer des vérifications de mise à jour programmatique.  
  
 Pour mettre à jour une application ClickOnce par programme, vous devez spécifier un emplacement pour les mises à jour.  Cette propriété est parfois désignée sous le nom de fournisseur de déploiement.  Pour plus d'informations sur la définition de cette propriété, consultez [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Vous pouvez également utiliser la technique décrite ci\-dessous pour déployer votre application à partir d'un emplacement et la mettre à jour à partir d'un autre.  Pour plus d'informations, consultez [How to: Specify an Alternate Location for Deployment Updates](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### Pour vérifier par programme l'existence de mises à jour  
  
1.  Créez une nouvelle application Windows Forms en utilisant vos outils de ligne de commande ou visuels par défaut.  
  
2.  Créez le bouton, l'élément de menu ou tout autre élément de l'interface utilisateur que vous souhaitez que vos utilisateurs sélectionnent pour vérifier les mises à jour.  Dans le gestionnaire d'événements de cet élément, appelez la méthode suivante pour vérifier et installer les mises à jour.  
  
     [!CODE [ClickOnceAPI#6](../CodeSnippet/VS_Snippets_Winforms/ClickOnceAPI#6)]  
  
3.  Compilez votre application.  
  
### Utilisation de Mage.exe pour déployer une application vérifiant des mises à jour par programme  
  
-   Suivez les instructions concernant le déploiement de votre application à l'aide de Mage.exe, comme indiqué dans [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Lorsque vous appelez Mage.exe pour générer le manifeste de déploiement, veillez à utiliser le commutateur de ligne de commande `providerUrl` et à spécifier l'URL où ClickOnce doit vérifier les mises à jour.  Si votre application est mise à jour à partir de [http:\/\/www.microsoft.com\/fr\/fr\/default.aspx](http://www.microsoft.com/fr/fr/default.aspx), par exemple, votre appel pour générer le manifeste de déploiement peut se présenter de la manière suivante :  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### Utilisation de MageUI.exe pour déployer une application vérifiant des mises à jour par programme  
  
-   Suivez les instructions concernant le déploiement de votre application à l'aide de Mage.exe, comme indiqué dans [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Sous l'onglet **Deployment Options**, définissez le champ **Start Location** sur le manifeste d'application dans lequel ClickOnce doit vérifier les mises à jour.  Sous l'onglet **Update Options**, désactivez la case à cocher **This application should check for updates**.  
  
## Sécurité .NET Framework  
 Votre application doit disposer des autorisations de type Confiance totale pour utiliser la mise à jour par programme.  
  
## Voir aussi  
 [How to: Specify an Alternate Location for Deployment Updates](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)