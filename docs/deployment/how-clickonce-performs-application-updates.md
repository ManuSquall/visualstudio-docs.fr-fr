---
title: Mises à jour de l’Application par ClickOnce | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbe09cfe546d947bf07334e9dd6468226884e9e3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-clickonce-performs-application-updates"></a>Mises à jour des applications par ClickOnce
ClickOnce utilise les informations de version de fichier spécifiées dans le manifeste de déploiement d’une application de décider s’il faut mettre à jour les fichiers de l’application. Après le début d’une mise à jour, ClickOnce utilise une technique appelée *mise à jour corrective du fichier* pour éviter le téléchargement redondant de fichiers d’application.  
  
## <a name="file-patching"></a>Mise à jour corrective du fichier  
 Lors de la mise à jour d’une application, ClickOnce ne télécharge pas tous les fichiers pour la nouvelle version de l’application, sauf si les fichiers ont été modifiés. Au lieu de cela, il compare les signatures de hachage des fichiers spécifiés dans le manifeste d’application pour l’application actuelle sur les signatures dans le manifeste pour la nouvelle version. Si les signatures d’un fichier sont différentes, ClickOnce télécharge la nouvelle version. Si les signatures correspondent, le fichier n’a pas changé d’une version à l’autre. Dans ce cas, ClickOnce copie le fichier existant et l’utilise dans la nouvelle version de l’application. Cette approche évite ClickOnce télécharger l’application entière, même si une ou deux fichiers ont été modifiés.  
  
 Correction de fichiers fonctionne également pour les assemblys qui sont téléchargés sur l’utilisation de la demande la <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> et <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> méthodes.  
  
 Si vous utilisez Visual Studio pour compiler votre application, il générera de nouvelles signatures de hachage pour tous les fichiers chaque fois que vous régénérez le projet entier. Dans ce cas, tous les assemblys seront téléchargés sur le client, même si seuls quelques assemblys a peut-être été modifié.  
  
 Correction de fichiers ne fonctionne pas pour les fichiers qui sont marqués comme données et stockés dans le répertoire de données. Ceux-ci sont toujours téléchargés, quelle que soit la signature de hachage du fichier. Pour plus d’informations sur le répertoire de données, consultez [l’accès aux données locales et distantes dans les Applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)