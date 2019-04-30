---
title: 'Erreur : Processus de travail de site Web a été interrompu par IIS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d89eabec0c199b1b8df7eeb78d0e629d4a70b2e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849999"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Erreur : Le processus Worker du site web a été arrêté par IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur a arrêté l’exécution du code sur le site web. Résultat : Internet Information Services (IIS) a supposé que le processus de travail avait cessé de répondre. Par conséquent, IIS a mis fin au processus de traitement.  
  
 Pour continuer le débogage, vous devez configurer IIS de sorte qu'il autorise la poursuite du processus de traitement. Ce message d'erreur n'apparaît pas avec les versions d'IIS antérieures à IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Pour configurer IIS 7 afin qu'il permette la poursuite du processus de travail  
  
1. Ouvrez la fenêtre **Outils d’administration**.  
  
   1. Cliquez sur **Démarrer**, puis choisissez **Panneau de configuration**.  
  
   2. Dans **Panneau de configuration**, sélectionnez **Basculer vers l’affichage classique**, si nécessaire, puis double-cliquez sur **Outils d’administration**.  
  
2. Dans la fenêtre **Outils d’administration**, double-cliquez sur **Gestionnaire des services Internet (IIS)**.  
  
    Le Gestionnaire des services IIS s'ouvre.  
  
3. Dans le volet **Connexions**, développez le nœud \<nom ordinateur> si nécessaire.  
  
4. Sous le nœud \<nom ordinateur>, cliquez sur **Pools d’applications**.  
  
5. Dans la liste **Pools d’applications**, cliquez avec le bouton droit sur le nom du pool dans lequel votre application est exécutée, puis cliquez sur **Paramètres avancés**.  
  
6. Dans la boîte de dialogue **Paramètres avancés**, localisez la section **Modèle de processus** et exécutez l’une des actions suivantes :  
  
   - Affectez la valeur **False** à **Ping activé**.  
  
   - Affectez une valeur supérieure à 90 secondes à **Temps de réponse maximum à un ping**.  
  
     Si vous affectez la valeur **False** à **Ping activé**, IIS cesse de vérifier si le processus de traitement est encore en cours d’exécution et maintient le processus de traitement actif jusqu’à ce que vous mettiez fin à votre processus débogué. L’affectation d’une valeur élevée au paramètre **Temps de réponse maximum à un ping** autorise IIS à continuer à superviser le processus de traitement.  
  
7. Cliquez sur **OK** pour fermer la boîte de dialogue **Paramètres avancés**.  
  
8. Fermez le Gestionnaire des services IIS et la fenêtre **Outils d’administration**.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs et résolution des problèmes du débogage distant](../debugger/remote-debugging-errors-and-troubleshooting.md)
