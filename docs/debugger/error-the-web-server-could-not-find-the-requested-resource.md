---
description: Pour des raisons de sécurité, IIS a retourné une erreur générique.
title: Le serveur Web n’a pas pu trouver la ressource demandée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e3509094e25447cedc6e46d7d811d65c39ea83e1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146611"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Erreur : le serveur web n’a pas trouvé la ressource demandée
Pour des raisons de sécurité, IIS a retourné une erreur générique.

Une des causes possibles est la configuration de la sécurité du serveur. IIS 6.0 et les versions antérieures utilisaient un programme supplémentaire, appelé URLScan, pour filtrer les requêtes suspectes et incorrectes. IIS 7.0 dispose du filtrage des demandes intégré pour le même objectif. Dans les deux cas, un filtrage des demandes restrictif peut empêcher Visual Studio à déboguer le serveur.

Une autre cause possible de cette erreur est que le service W3SVC pour IIS n’est pas démarré. Vérifiez que ce service est démarré (grisé) dans la fenêtre Services (*services. msc*).

Cette erreur peut avoir de nombreuses causes supplémentaires. Certaines des causes courantes incluent un problème lié à l'installation ou la configuration d'IIS, à la configuration de site Web, ou aux autorisations du système de fichiers. Vous pouvez essayer d'accéder à la ressource avec un navigateur. Selon la façon dont IIS est configuré, vous devrez peut-être utiliser un navigateur local sur le serveur ou examiner le journal des erreurs IIS pour obtenir un message d’erreur détaillé.

 Pour plus d’informations sur la résolution des problèmes liés à IIS, consultez [Administration et gestion IIS](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).

## <a name="see-also"></a>Voir aussi
- [Erreur : le serveur Web a été verrouillé et bloque le verbe de débogage](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
