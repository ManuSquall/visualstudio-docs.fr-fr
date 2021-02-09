---
title: Le processus de travail de site Web a été arrêté par IIS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cf7832d71ab86c6dab973a07dbc46217274cb83b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870894"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Erreur : le processus de travail de site Web a été interrompu par IIS.
Le débogueur a arrêté l’exécution du code sur le site web. Résultat : Internet Information Services (IIS) a supposé que le processus de travail avait cessé de répondre. Par conséquent, IIS a mis fin au processus de traitement.

 Pour continuer le débogage, vous devez configurer IIS de sorte qu'il autorise la poursuite du processus de traitement. Ce message d'erreur n'apparaît pas avec les versions d'IIS antérieures à IIS 7.

### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Pour configurer IIS 7 afin qu'il permette la poursuite du processus de travail

1. Ouvrez la fenêtre **Outils d’administration**.

   1. Cliquez sur **Démarrer**, puis choisissez **Panneau de configuration**.

   2. Dans **Panneau de configuration**, sélectionnez **Basculer vers l’affichage classique**, si nécessaire, puis double-cliquez sur **Outils d’administration**.

2. Dans la fenêtre **Outils d’administration**, double-cliquez sur **Gestionnaire des services Internet (IIS)**.

    Le Gestionnaire des services IIS s'ouvre.

3. Dans le volet **connexions** , développez le \<computer name> nœud si nécessaire.

4. Sous le \<computer name> nœud, cliquez sur **pools d’applications**.

5. Dans la liste **Pools d’applications**, cliquez avec le bouton droit sur le nom du pool dans lequel votre application est exécutée, puis cliquez sur **Paramètres avancés**.

6. Dans la boîte de dialogue **Paramètres avancés**, localisez la section **Modèle de processus** et exécutez l’une des actions suivantes :

   - Affectez la valeur **False** à **Ping activé**.

   - Affectez une valeur supérieure à 90 secondes à **Temps de réponse maximum à un ping**.

     Si vous affectez la valeur **False** à **Ping activé**, IIS cesse de vérifier si le processus de traitement est encore en cours d’exécution et maintient le processus de traitement actif jusqu’à ce que vous mettiez fin à votre processus débogué. L’affectation d’une valeur élevée au paramètre **Temps de réponse maximum à un ping** autorise IIS à continuer à superviser le processus de traitement.

7. Cliquez sur **OK** pour fermer la boîte de dialogue **Paramètres avancés** .

8. Fermez le Gestionnaire des services IIS et la fenêtre **Outils d’administration**.

## <a name="see-also"></a>Voir aussi
- [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)