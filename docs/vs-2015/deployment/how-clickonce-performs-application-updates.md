---
title: Mises à jour de l’Application par ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8011447de248c2dbcdbd513dc4e51106ceb3a568
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508663"
---
# <a name="how-clickonce-performs-application-updates"></a>Mises à jour des applications par ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [comment ClickOnce exécute Application mises à jour](https://docs.microsoft.com/visualstudio/deployment/how-clickonce-performs-application-updates).  
  
ClickOnce utilise les informations de version de fichier spécifiées dans le manifeste de déploiement d’une application pour décider s’il faut mettre à jour les fichiers de l’application. Après une mise à jour commence, ClickOnce utilise une technique appelée *mise à jour corrective du fichier* pour éviter le téléchargement redondant de fichiers d’application.  
  
## <a name="file-patching"></a>Mise à jour corrective du fichier  
 Lors de la mise à jour une application, ClickOnce ne télécharge pas tous les fichiers pour la nouvelle version de l’application, sauf si les fichiers ont été modifiés. Au lieu de cela, il compare les signatures de hachage des fichiers spécifiés dans le manifeste d’application pour l’application actuelle contre les signatures dans le manifeste pour la nouvelle version. Si les signatures d’un fichier sont différentes, ClickOnce télécharge la nouvelle version. Si les signatures correspondent, le fichier n’a pas changé d’une version à l’autre. Dans ce cas, ClickOnce copie le fichier existant et l’utilise dans la nouvelle version de l’application. Cette approche évite ClickOnce télécharger l’application entière à nouveau, même si seulement une ou deux fichiers ont été modifiés.  
  
 Mise à jour corrective du fichier fonctionne également pour les assemblys qui sont téléchargés sur l’utilisation de la demande la <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> et <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> méthodes.  
  
 Si vous utilisez Visual Studio pour compiler votre application, il générera de nouvelles signatures de hachage pour tous les fichiers chaque fois que vous régénérez le projet entier. Dans ce cas, tous les assemblys sont téléchargées vers le client, bien que seuls quelques assemblys a peut-être changé.  
  
 Mise à jour corrective du fichier ne fonctionne pas pour les fichiers qui sont marqués en tant que données et stockées dans le répertoire de données. Ceux-ci sont toujours téléchargés, quel que soit la signature de hachage du fichier. Pour plus d’informations sur le répertoire de données, consultez [l’accès aux données locales et distantes dans les Applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



