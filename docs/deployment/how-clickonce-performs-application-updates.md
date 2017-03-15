---
title: "How ClickOnce Performs Application Updates | Microsoft Docs"
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
  - "updates, ClickOnce"
  - "ClickOnce deployment, updates"
  - "deploying applications [ClickOnce], application updates"
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How ClickOnce Performs Application Updates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce utilise les informations de version de fichier spécifiées dans le manifeste de déploiement d'une application pour décider s'il convient de mettre à jour les fichiers de l'application.  Après le lancement d'une mise à jour, ClickOnce utilise une technique appelée *correction de fichiers* pour éviter le téléchargement redondant de fichiers d'application.  
  
## Correction de fichiers  
 Lors de la mise à jour d'une application, ClickOnce ne télécharge pas tous les fichiers pour la nouvelle version de l'application, à moins que les fichiers aient changé.  Au lieu de cela, ClickOnce compare les signatures de hachage des fichiers spécifiés dans le manifeste d'application pour l'application en cours aux signatures du manifeste pour la nouvelle version.  Si les signatures d'un fichier sont différentes, ClickOnce télécharge la nouvelle version.  Si les signatures correspondent, le fichier n'a pas été modifié d'une version à l'autre.  Dans ce cas, ClickOnce copie le fichier existant et l'utilise dans la nouvelle version de l'application.  Cette approche évite à ClickOnce de télécharger une nouvelle fois l'application dans son intégralité, même si un ou deux fichiers seulement ont changé.  
  
 La correction de fichiers fonctionne également pour les assemblys téléchargés à la demande à l'aide des méthodes <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> et <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A>.  
  
 Si vous utilisez Visual Studio pour compiler votre application, il générera de nouvelles signatures de hachage pour tous les fichiers à chaque régénération du projet dans son intégralité.  Dans ce cas, tous les assemblys seront téléchargés sur le client, même si seuls quelques assemblys ont été modifiés.  
  
 La correction de fichiers ne fonctionne pas pour les fichiers marqués comme données et stockés dans le répertoire de données.  Ceux\-ci sont toujours téléchargés, quelle que soit la signature de hachage du fichier.  Pour plus d'informations sur le répertoire de données, consultez [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## Voir aussi  
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)