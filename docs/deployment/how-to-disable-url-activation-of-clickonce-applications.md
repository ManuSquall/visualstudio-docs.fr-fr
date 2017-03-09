---
title: "How to: Disable URL Activation of ClickOnce Applications | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "disallowUrlActivation"
  - "URL activation, ClickOnce applications"
  - "ClickOnce deployment, URL activation"
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Disable URL Activation of ClickOnce Applications
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En règle générale, une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se lance automatiquement immédiatement après son installation à partir d'un serveur web.  Pour des raisons de sécurité, vous pouvez décider de désactiver ce comportement et d'inviter plutôt les utilisateurs à lancer l'application à partir du menu **Démarrer**.  La procédure suivante décrit comment désactiver l'activation d'URL.  
  
 Cette technique peut être utilisée uniquement pour les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installées sur l'ordinateur de l'utilisateur à partir d'un serveur web.  Elle ne peut pas être utilisée pour les applications en ligne uniquement, qui peuvent être lancées uniquement à l'aide de leur URL.  Pour plus d'informations sur la différence entre les applications en ligne uniquement et les applications installées, consultez [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Cette procédure utilise l'outil du [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] MageUI.exe.  Pour plus d'informations sur cet outil, consultez [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  Vous pouvez également effectuer cette procédure avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Procédure  
  
#### Pour désactiver l'activation d'URL pour votre application  
  
1.  Ouvrez votre manifeste de déploiement dans MageUI.exe.  Si vous n'en n'avez pas encore créé un, suivez les étapes de la [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Sélectionnez l'onglet **Options de déploiement**.  
  
3.  Décochez la case **Exécuter automatiquement l'application après l'installation**.  
  
4.  Enregistrez et signez le manifeste.  
  
## Voir aussi  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)