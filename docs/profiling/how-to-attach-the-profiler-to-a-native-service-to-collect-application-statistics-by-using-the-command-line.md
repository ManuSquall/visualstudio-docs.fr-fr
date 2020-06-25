---
title: VSPerfCmd-attacher le profileur au service natif pour récupérer les statistiques de l’application
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: f45d08a82bdc3f6807f9a4d5a0cb31dc157e4c9c
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328657"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>Guide pratique pour attacher le profileur à un service natif et collecter des statistiques d’application en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à un service natif et collecter des statistiques de performances à l’aide de la méthode d’échantillonnage.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

 Lorsque le profileur est attaché au service, vous pouvez suspendre et reprendre la collecte de données.

 Pour mettre fin à une session de profilage, vous devez détacher le profileur du service et l’arrêter explicitement.

## <a name="start-the-application-with-the-profiler"></a>Démarrer l’application avec le profileur
 Pour attacher le profileur à un service natif, utilisez les options [/start](../profiling/start.md) et [/attach](../profiling/attach.md) de **VSPerfCmd.exe** pour initialiser le profileur et l’attacher à l’application cible. Vous pouvez spécifier **/start** et **/attach** et leurs options respectives sur une même ligne de commande. Vous pouvez également ajouter l’option [/globaloff](../profiling/globalon-and-globaloff.md) pour suspendre la collecte des données au démarrage de l’application cible. Vous pouvez ensuite utiliser [/globalon](../profiling/globalon-and-globaloff.md) pour commencer à collecter les données.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Pour attacher le profileur à un service natif

1. Si nécessaire, démarrez le service.

2. Ouvrir une fenêtre d’invite de commandes.

3. Démarrez le profileur. Tapez :

    **VSPerfCmd/start : exemple**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - L’option **/Start : Sample** Initialise le profileur.

   - L’option **/Output :** `OutputFile` est requise avec **/Start**. `OutputFile`Spécifie le nom et l’emplacement des données de profilage (.* vsp*).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:sample**.

   > [!NOTE]
   > Les options **/user** et **/crosssession** sont généralement nécessaires pour les services.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si l’application s’exécute dans une autre session. L’ID de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl). |

4. Attachez le profileur au service. Tapez :

    **VSPerfCmd/Attach :** `PID` [`Sample Event`]

    `PID` spécifie l’ID de processus de l’application cible. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.

    Par défaut, les données de performances sont échantillonnées tous les 10 000 000 cycles d’horloge ininterrompus du processeur. Ceci correspond environ à une fois toutes les 10 secondes sur un processeur à 1 GHz. Vous pouvez spécifier l’une des options suivantes pour modifier l’intervalle de cycle d’horloge ou pour spécifier un autre événement d’échantillonnage.

   |Événement d’échantillonnage|Description|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Remplace l’intervalle d’échantillonnage par le nombre de cycles d’horloge sans interruption spécifié par `Interval`.|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Remplace l’événement d’échantillonnage par les erreurs de page. Si `Interval` est spécifié, définit le nombre d’erreurs de page entre chaque échantillon. La valeur par défaut est 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Remplace l’événement d’échantillonnage par des appels système du processus vers le noyau du système d’exploitation (syscalls). Si `Interval` est spécifié, définit le nombre d’appels entre chaque échantillon. La valeur par défaut est 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Remplace l’événement et l’intervalle d’échantillonnage par le compteur de performances du processeur et l’intervalle spécifiés dans `Config`.|

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution de l’application cible, vous pouvez utiliser les options de *VSPerfCmd.exe* pour démarrer et arrêter l’écriture des données dans le fichier de données du profileur. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options **VSPerfCmd** suivantes démarrent et arrêtent la collecte de données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |**/Attach :** { `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[ : { `PID`&#124;`ProcName` }]|**/attach** commence à collecter des données pour le processus spécifié par l’ID ou le nom de processus. **/detach** arrête la collecte des données pour le processus spécifié, ou pour tous les processus si aucun processus n’est spécifié.|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour mettre fin à une session de profilage, vous devez détacher le profileur du service et l’arrêter explicitement. Vous pouvez arrêter la collecte des données d’un service natif profilé avec la méthode d’accès concurrentiel en arrêtant le service ou en appelant l’option **VSPerfCmd /detach**. Vous appelez ensuite l’option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Effectuez une des opérations suivantes pour détacher le profileur de l’application cible :

    - Arrête le service.

         -ou-

    - Tapez **VSPerfCmd/detach**

2. Fermez le profileur. Tapez :

     **VSPerfCmd /shutdown**

## <a name="see-also"></a>Voir aussi
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
- [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)
