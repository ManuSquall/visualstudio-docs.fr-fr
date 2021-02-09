---
title: Attacher le profileur à un service natif pour obtenir des données de concurrence
description: Utilisez Visual Studio Outils de profilage à partir de la ligne de commande pour collecter des données de concurrence de processus et de thread à partir d’un service natif (C/C++).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 301e507e7debb04aab25b30e0a4e8f234f57a46b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881631"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line-vsperfcmd"></a>Comment : attacher le profileur à un service natif pour collecter des données d’accès concurrentiel à l’aide de la ligne de commande (VSPerfCmd)
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à un service natif (C/C++) et collecter des données de concurrence sur les processus et les threads à l’aide de la méthode d’échantillonnage.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

 Lorsque le profileur est attaché au service, vous pouvez suspendre et reprendre la collecte de données. Pour permettre l’arrêt d’une session de profilage, le profileur ne doit plus être attaché au service. Profiler doit être arrêté explicitement.

## <a name="attach-the-profiler"></a>Attacher le profileur
 Pour attacher le profileur à un service natif, utilisez les options **VSPerfCmd/start** et **/attach** pour initialiser le profileur et l’attacher à l’application cible. Vous pouvez spécifier **/start** et **/attach** et leurs options respectives sur une même ligne de commande. Vous pouvez également ajouter l’option **/globaloff** pour suspendre la collecte des données au démarrage de l’application cible. Ensuite, utilisez **/globalon** pour commencer à collecter les données.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Pour attacher le profileur à un service natif

1. Si le service n’est pas en cours d’exécution, démarrez-le.

2. Démarrez le profileur en tapant ce qui suit à l’invite de commandes :

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start : concurrence/output :** `OutputFile` [ `Options` ]

   - L’option [/Output](../profiling/output.md)**:** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options du tableau suivant avec l’option **/start**.

   > [!NOTE]
   > La plupart des services nécessitent les options **/user** et **/crosssession**.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`UserName` | Spécifie les noms de domaine et d’utilisateur facultatifs du compte qui doit obtenir l’accès au profileur. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est 500. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl). |

3. Attachez le profileur au service en tapant la commande suivante dans la fenêtre d’invite de commandes :

    **VSPerfCmd /attach:** `PID`

    `PID` spécifie l’ID ou le nom de processus de l’application cible. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant que l’application cible est en cours d’exécution, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier avec les options de *VSPerfCmd.exe* . Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options du tableau suivant permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach** commence à collecter des données pour le processus spécifié par l’ID de processus (`PID`) ou le nom de processus (*ProcName*). **/detach** arrête la collecte des données pour le processus spécifié ou pour tous les processus, si aucun processus n’est spécifié.|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit pas être en train de collecter des données. Vous pouvez arrêter la collecte des données d’un service natif profilé avec la méthode d’accès concurrentiel en arrêtant le service ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Détachez le profileur de l’application cible en arrêtant le service ou en tapant la commande suivante dans la fenêtre d’invite de commandes :

     Tapez **VSPerfCmd/detach**

2. Fermez le profileur en tapant ce qui suit à l’invite de commandes :

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)
