---
title: Attacher le profileur à une application native et collecter des statistiques d’application
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 9d463413833ad476b8d6ad90369f53267e3f7cff
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328666"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Guide pratique pour attacher le profileur à une application autonome native et collecter des statistiques d’application en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à une application autonome native (cliente) en cours d’exécution et collecter des statistiques de performances à l’aide de la méthode d’échantillonnage.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

 Quand le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte des données. Pour terminer une session de profilage, le profileur ne doit plus être attaché à l’application et doit être arrêté explicitement.

## <a name="attach-the-profiler"></a>Attacher le profileur
 Pour attacher le profileur à une application cible à l’aide du profileur, utilisez les options **VSPerfCmd/start** et **/Attach** pour initialiser le profileur et l’attacher à l’application cible. Vous pouvez spécifier **/start** et **/attach** et leurs options respectives sur une même ligne de commande. Vous pouvez également ajouter l’option **/globaloff** pour suspendre la collecte des données au démarrage de l’application cible. Ensuite, utilisez **/globalon** pour commencer à collecter les données.

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Pour attacher le profileur à une application .NET Framework en cours d’exécution

1. Ouvrez une fenêtre d’invite de commandes.

2. Démarrez le profileur. Tapez :

    **VSPerfCmd/start : exemple/output :** `OutputFile` [`Options`]

   - L’option [/start](../profiling/start.md)**:sample** initialise le profileur.

   - L’option [/Output](../profiling/output.md)**:** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:sample**.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’identificateur de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un (.* fichier ETL*). |

3. Attachez le profileur à l’application cible. Tapez :

    **VSPerfCmd**  [/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [ `Sample Event` ]

    `PID` spécifie l’ID de processus de l’application cible. `ProcessName` spécifie le nom du processus. Notez que si vous spécifiez `ProcessName` et que plusieurs processus de même nom sont en cours d’exécution, les résultats sont imprévisibles. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.

    Par défaut, les données de performances sont échantillonnées tous les 10 000 000 cycles d’horloge ininterrompus du processeur. C’est-à-dire environ 100 fois par seconde sur un processeur de 1 GHz. Vous pouvez spécifier l’une des options suivantes pour modifier l’intervalle de cycle d’horloge ou spécifier un autre événement d’échantillonnage.

   |Exemple d’événement|Description|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Remplace l’intervalle d’échantillonnage par le nombre de cycles d’horloge ininterrompus spécifiés par `Interval`.|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Remplace l’événement d’échantillonnage par les erreurs de page. Si `Interval` est spécifié, définit le nombre d’erreurs de page entre chaque échantillon. La valeur par défaut est 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Remplace l’événement d’échantillonnage par des appels système du processus vers le noyau du système d’exploitation (syscalls). Si `Interval` est spécifié, définit le nombre d’appels entre chaque échantillon. La valeur par défaut est 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Remplace l’événement et l’intervalle d’échantillonnage par le compteur de performances du processeur et l’intervalle spécifié dans `Config`.|

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Lorsque l’application cible est en cours d’exécution, vous pouvez utiliser *VSPerfCmd.exe* options pour démarrer et arrêter l’écriture de données dans le fichier de données du profileur. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options **VSPerfCmd** suivantes démarrent et arrêtent la collecte de données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par `PID`.|
    |[/Attach](../profiling/attach.md) **:** `PID` [/Detach](../profiling/detach.md)|**/attach** commence à collecter des données pour le processus spécifié par `PID`. **/detach** arrête la collecte des données pour tous les processus.|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché à un processus profilé et doit être arrêté explicitement. Vous pouvez détacher le profileur d’une application profilée avec la méthode d’échantillonnage en fermant l’application ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /off** efface les variables d’environnement de profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Effectuez l’une des opérations suivantes pour détacher le profileur de l’application cible.

    - Tapez **VSPerfCmd/detach**

         -ou-

    - Fermez l’application cible.

2. Fermez le profileur. Tapez :

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

3. (Facultatif) Effacez les variables d’environnement de profilage. Tapez :

     **VSPerfClrEnv /off**

## <a name="see-also"></a>Voir aussi
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)
