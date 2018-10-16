---
title: 'Erreur : Le serveur Web n’a pas trouvé la ressource demandée | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8769c84237d877f02b7c9d3d02c6391f9e955ff3
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100976"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Erreur : le serveur web n’a pas trouvé la ressource demandée
Pour des raisons de sécurité, IIS a retourné une erreur générique.  

Une des causes possibles est la configuration de la sécurité du serveur. IIS 6.0 et les versions antérieures utilisaient un programme supplémentaire, appelé URLScan, pour filtrer les requêtes suspectes et incorrectes. IIS 7.0 dispose du filtrage des demandes intégré pour le même objectif. Dans les deux cas, un filtrage des demandes restrictif peut empêcher Visual Studio à déboguer le serveur.  

Une autre cause possible de cette erreur est que le service W3SVC pour IIS n’est pas démarré. Vérifiez que ce service est démarré (grisé) dans la fenêtre Services (*services.msc*).

Il existe de nombreuses raisons supplémentaires de cette erreur. Certaines des causes courantes incluent un problème lié à l’installation ou la configuration d’IIS, à la configuration de site web, ou aux autorisations du système de fichiers. Vous pouvez essayer d'accéder à la ressource avec un navigateur. Selon la façon dont IIS est configuré, vous devrez peut-être utiliser un navigateur local sur le serveur ou inspecter le journal des erreurs IIS pour obtenir un message d’erreur détaillé.  
  
 Pour plus d’informations sur la résolution des problèmes d’IIS, consultez [gestion d’IIS et l’Administration](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Voir aussi  
 [Erreur : le serveur web est verrouillé et bloque l’exécution du verbe DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)