---
title: Mises à jour de l’Application par ClickOnce | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 5fc3414660f206aa8f83179e61ed9aa2dcc0098b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845601"
---
# <a name="how-clickonce-performs-application-updates"></a>Mises à jour des applications par ClickOnce
ClickOnce utilise les informations de version de fichier spécifiées dans le manifeste de déploiement d’une application pour décider s’il faut mettre à jour les fichiers de l’application. Après une mise à jour commence, ClickOnce utilise une technique appelée *mise à jour corrective du fichier* pour éviter le téléchargement redondant de fichiers d’application.  
  
## <a name="file-patching"></a>Mise à jour corrective du fichier  
 Lors de la mise à jour une application, ClickOnce ne télécharge pas tous les fichiers pour la nouvelle version de l’application, sauf si les fichiers ont été modifiés. Au lieu de cela, il compare les signatures de hachage des fichiers spécifiés dans le manifeste d’application pour l’application actuelle contre les signatures dans le manifeste pour la nouvelle version. Si les signatures d’un fichier sont différentes, ClickOnce télécharge la nouvelle version. Si les signatures correspondent, le fichier n’a pas changé d’une version à l’autre. Dans ce cas, ClickOnce copie le fichier existant et l’utilise dans la nouvelle version de l’application. Cette approche évite ClickOnce télécharger l’application entière à nouveau, même si seulement une ou deux fichiers ont été modifiés.  
  
 Mise à jour corrective du fichier fonctionne également pour les assemblys qui sont téléchargés sur l’utilisation de la demande la <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> et <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> méthodes.  
  
 Si vous utilisez Visual Studio pour compiler votre application, il générera de nouvelles signatures de hachage pour tous les fichiers chaque fois que vous régénérez le projet entier. Dans ce cas, tous les assemblys sont téléchargées vers le client, bien que seuls quelques assemblys a peut-être changé.  
  
 Mise à jour corrective du fichier ne fonctionne pas pour les fichiers qui sont marqués en tant que données et stockées dans le répertoire de données. Ceux-ci sont toujours téléchargés, quel que soit la signature de hachage du fichier. Pour plus d’informations sur le répertoire de données, consultez [accéder aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)