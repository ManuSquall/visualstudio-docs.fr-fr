---
title: "Manifestes d&#39;application et de d&#233;ploiement dans les solutions Office | Microsoft Docs"
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
  - "manifestes (développement Office dans Visual Studio)"
  - "manifestes de déploiement (développement Office dans Visual Studio)"
  - "manifestes d'application (développement Office dans Visual Studio)"
  - "assemblys (développement Office dans Visual Studio), mise à jour"
ms.assetid: 4e9abc7c-ef9f-4cb2-a7a9-c95c5f4a1fb7
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Manifestes d&#39;application et de d&#233;ploiement dans les solutions Office
  Un manifeste d'application est un fichier XML qui fournit les informations utilisées par une solution Office pour localiser ses assemblys et les mettre à jour. Un manifeste d'application peut être utilisé avec un manifeste de déploiement, qui est un fichier XML stocké sur le serveur fournissant les informations nécessaires à la localisation de la version la plus récente du manifeste d'application et des assemblys.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Structure de manifeste pour les solutions Office  
 Pour les solutions Microsoft Office créées à l'aide des Outils de développement Office dans Visual Studio, tous les manifestes sont basés sur le schéma ClickOnce standard. Quand vous déployez vos solutions Office, les manifestes d’application pour les projets au niveau du document et les projets de complément VSTO se trouvent dans le cache ClickOnce. Les manifestes de déploiement ne sont pas copiés sur l'ordinateur client.  
  
 Pour plus d’informations sur le contenu des manifestes d’application et de déploiement des projets Office, consultez [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md) et [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
## Création de manifestes d'application et de déploiement  
 Les manifestes d'application sont créés automatiquement dans le cadre du processus de génération. Chaque fois que vous générez un projet au niveau du document, l'emplacement du manifeste de déploiement est incorporé dans le document comme une propriété de document personnalisée. Pour les compléments VSTO, l’emplacement du manifeste de déploiement est stocké dans le Registre.  
  
 Pour plus d’informations sur l’**Assistant Publication**, consultez [Déploiement d'une solution Office à l'aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Pour plus d’informations sur la façon dont les manifestes fonctionnent avec les solutions Office, consultez [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md).  
  
## Voir aussi  
 [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)   
 [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)  
  
  