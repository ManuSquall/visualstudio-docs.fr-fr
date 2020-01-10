---
title: 'Erreur : le serveur Web n’a pas pu trouver la ressource demandée | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 555bb56ee84b7bc48f6b6453c11daef366f97e49
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845115"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Erreur : le serveur web n’a pas trouvé la ressource demandée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour des raisons de sécurité, IIS a retourné une erreur générique.  
  
 Une des causes possibles est la configuration de la sécurité du serveur. IIS 6.0 et les versions antérieures utilisaient un programme supplémentaire, appelé URLScan, pour filtrer les requêtes suspectes et incorrectes. IIS 7.0 dispose du filtrage des demandes intégré pour le même objectif. Dans les deux cas, un filtrage des demandes restrictif peut empêcher Visual Studio à déboguer le serveur.  
  
 Cette erreur peut se produire pour de nombreuses raisons. Certaines des causes courantes incluent un problème lié à l'installation ou la configuration d'IIS, à la configuration de site Web, ou aux autorisations du système de fichiers. Vous pouvez essayer d'accéder à la ressource avec un navigateur. Selon comment IIS est configuré, vous devrez peut-être utiliser un navigateur local sur le serveur ou examiner le journal des erreurs IIS pour obtenir un message d'erreur détaillé.  
  
 Pour plus d’informations sur la résolution des problèmes liés à IIS, consultez [Administration et gestion IIS](https://www.iis.net/learn/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Voir aussi  
   de l' [outil de sécurité URLScan](/iis/extensions/working-with-urlscan/urlscan-3-reference)  
 [Erreur : le serveur web est verrouillé et bloque l’exécution du verbe DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
