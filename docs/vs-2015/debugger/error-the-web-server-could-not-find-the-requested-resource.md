---
title: 'Erreur : Le serveur Web n’a pas trouvé la ressource demandée | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f490006d21f51f48cd8b2d97da262015ab170f39
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808295"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Erreur : le serveur web n’a pas trouvé la ressource demandée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour des raisons de sécurité, IIS a retourné une erreur générique.  
  
 Une des causes possibles est la configuration de la sécurité du serveur. IIS 6.0 et les versions antérieures utilisaient un programme supplémentaire, appelé URLScan, pour filtrer les requêtes suspectes et incorrectes. IIS 7.0 dispose du filtrage des demandes intégré pour le même objectif. Dans les deux cas, un filtrage des demandes restrictif peut empêcher Visual Studio à déboguer le serveur.  
  
 Cette erreur peut se produire pour de nombreuses raisons. Certaines des causes courantes incluent un problème lié à l'installation ou la configuration d'IIS, à la configuration de site Web, ou aux autorisations du système de fichiers. Vous pouvez essayer d'accéder à la ressource avec un navigateur. Selon comment IIS est configuré, vous devrez peut-être utiliser un navigateur local sur le serveur ou examiner le journal des erreurs IIS pour obtenir un message d'erreur détaillé.  
  
 Pour plus d’informations sur la résolution des problèmes d’IIS, consultez [gestion d’IIS et l’Administration](http://go.microsoft.com/fwlink/?LinkId=255872).  
  
## <a name="see-also"></a>Voir aussi  
 [Outil de sécurité UrlScan](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [Erreur : le serveur web est verrouillé et bloque l’exécution du verbe DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)



