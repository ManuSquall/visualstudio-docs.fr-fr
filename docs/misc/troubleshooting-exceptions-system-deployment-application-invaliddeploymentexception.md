---
title: "D&#233;pannage des exceptions&#160;: System.Deployment.Application.InvalidDeploymentException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidDeploymentException (classe)"
ms.assetid: 4361e053-8eaf-44e3-b8ac-95516d8d1832
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Deployment.Application.InvalidDeploymentException
Une exception <xref:System.Deployment.Application.InvalidDeploymentException> est levée lorsque l'application ou ses manifestes d'application et de déploiement ne sont pas valides.  
  
## Conseils associés  
 **Assurez\-vous que les manifestes de cette application sont valides.**  
 Un manifeste d'application est un fichier XML qui décrit et identifie les assemblys côte à côte partagés et privés auxquels une application doit se lier au moment de l'exécution. Il doit s'agir des mêmes versions d'assembly qui ont été utilisées pour tester l'application. Les manifestes d'application peuvent également décrire les métadonnées de fichiers privés pour l'application.  
  
 **Utilisez la fonctionnalité ClickOnce pour déployer l'application.**  
 Utilisez ClickOnce pour publier des applications Windows sur un serveur Web ou un partage de fichier réseau pour simplifier l'installation. Pour plus d'informations, consultez [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
## Voir aussi  
 <xref:System.Deployment.Application.InvalidDeploymentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)   
 [Déploiement ClickOnce pour les Windows Forms](../Topic/ClickOnce%20Deployment%20for%20Windows%20Forms.md)