---
title: Comment ClickOnce effectue des mises à jour d’application | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9217558c68d47ef8f2bf34b10db16463ee76f857
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900019"
---
# <a name="how-clickonce-performs-application-updates"></a>Mises à jour des applications par ClickOnce
ClickOnce utilise les informations de version de fichier spécifiées dans le manifeste de déploiement d’une application pour décider s’il faut mettre à jour les fichiers de l’application. Après le début d’une mise à jour, ClickOnce utilise une technique appelée mise à jour *corrective des fichiers* pour éviter le téléchargement redondant des fichiers d’application.

## <a name="file-patching"></a>Mise à jour corrective des fichiers
 Lors de la mise à jour d’une application, ClickOnce ne télécharge pas tous les fichiers de la nouvelle version de l’application, sauf si les fichiers ont été modifiés. Au lieu de cela, il compare les signatures de hachage des fichiers spécifiés dans le manifeste d’application pour l’application actuelle aux signatures du manifeste pour la nouvelle version. Si les signatures d’un fichier sont différentes, ClickOnce télécharge la nouvelle version. Si les signatures correspondent, le fichier n’a pas changé d’une version à l’autre. Dans ce cas, ClickOnce copie le fichier existant et l’utilise dans la nouvelle version de l’application. Cette approche empêche ClickOnce de télécharger à nouveau l’application entière, même si un seul ou deux fichiers ont été modifiés.

 La mise à jour corrective des fichiers fonctionne également pour les assemblys qui sont téléchargés à la demande à l’aide des <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> méthodes et.

 Si vous utilisez Visual Studio pour compiler votre application, il génère de nouvelles signatures de hachage pour tous les fichiers chaque fois que vous reconstruisez le projet entier. Dans ce cas, tous les assemblys sont téléchargés sur le client, même si seuls quelques assemblys peuvent avoir changé.

 La mise à jour corrective des fichiers ne fonctionne pas pour les fichiers marqués comme données et stockés dans le répertoire de données. Ils sont toujours téléchargés, quelle que soit la signature de hachage du fichier. Pour plus d’informations sur le répertoire de données, consultez [accéder aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Voir aussi
- [Choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)