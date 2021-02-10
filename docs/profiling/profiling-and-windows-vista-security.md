---
title: Profilage et sécurité de Windows Vista | Microsoft Docs
description: En fonction des paramètres des autorisations d’accès utilisateur disponibles, un utilisateur individuel peut avoir l’autorisation de sécurité pour profiler un processus sur cet ordinateur.
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0419ae09f2b43b396062fc8a3232b0a63c81483c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936390"
---
# <a name="profiling-and-windows-vista-security"></a>Profilage et sécurité Windows Vista

Selon les paramètres d’autorisation d’accès utilisateur de [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] mis à disposition par l’administrateur d’un ordinateur, un utilisateur individuel peut disposer de l’autorisation de sécurité pour profiler un processus sur cet ordinateur. Les exemples suivants montrent les différences possibles entre les utilisateurs :

- Certains utilisateurs peuvent accéder à des fonctionnalités de profilage avancées quand l’administrateur a défini le démarrage du pilote et du service.

- Les utilisateurs de domaine peuvent accéder seulement au profilage d’échantillon.

- Certains utilisateurs peuvent refuser l’accès au profilage à tous les autres utilisateurs.

  Pour plus d’informations, consultez les options d’administration dans [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Profilage intersession

Le *profilage intersession* est la capacité à profiler un processus qui s’exécute dans une autre session utilisateur. Par exemple, la plupart des services s’exécutent dans la session 0, et les utilisateurs ne peuvent pas exécuter directement dans la session 0. Avec le bouton **Attacher au processus** de la barre d’outils de l’Explorateur de performances ou de l’option `/attach` de l’outil en ligne de commande VSPerfCmd, vous pouvez profiler la plupart des processus dans d’autres sessions utilisateur.

Pour consulter la liste des processus disponibles, définissez les options de visibilité du profilage interprocessus. Ces options sont disponibles dans la fenêtre **Attacher au processus** qui s’affiche quand vous sélectionnez **Attacher au processus** :

- **Afficher les processus de tous les utilisateurs**

  Quand cette option n’est pas sélectionnée, la liste montre seulement les processus dont l’utilisateur actuel est propriétaire. Sinon, la liste montre les processus de tous les utilisateurs.

- **Afficher les processus de toutes les sessions**

  Quand cette option n’est pas sélectionnée, la liste montre les processus de la session active. Sinon, la liste montre les processus de toutes les sessions.

## <a name="see-also"></a>Voir aussi

- [Vues d'ensemble](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Comment : attacher à un processus en cours d’exécution](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
