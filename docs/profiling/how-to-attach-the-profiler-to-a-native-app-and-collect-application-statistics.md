---
title: Attacher le profileur à une application native et collecter des statistiques d’application
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: a30a53cc6ca04d3a45f5264de6e9481b3603b53b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042749"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Procédure : Attacher le profileur à une application autonome native et collecter des statistiques d’application en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à une application autonome native (cliente) en cours d’exécution et collecter des statistiques de performances à l’aide de la méthode d’échantillonnage.  

> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
>  Pour obtenir le chemin d’accès des outils de profilage, voir [Spécifier le chemin d’accès des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.  

 Quand le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte des données. Pour terminer une session de profilage, le profileur ne doit plus être attaché à l’application et doit être arrêté explicitement.  

## <a name="attach-the-profiler"></a>Attacher le profileur  
 Pour initialiser le profileur et l’attacher à l’application cible, utilisez les options **VSPerfCmd/start** et **/attach**. Vous pouvez spécifier **/start** et **/attach** et leurs options respectives sur une même ligne de commande. Vous pouvez également ajouter l’option **/globaloff** pour suspendre la collecte des données au démarrage de l’application cible. Ensuite, utilisez **/globalon** pour commencer à collecter les données.  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Pour attacher le profileur à une application .NET Framework en cours d’exécution  

1. Ouvrez une fenêtre Invite de commandes.  

2. Démarrez le profileur. Type :  

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]  

   - L’option [/start](../profiling/start.md)**:sample** initialise le profileur.  

   - L’option [/output](../profiling/output.md)**:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).  

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:sample**.  

   | Option | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows. |
   | [/crosssession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’identificateur de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/automark](../profiling/automark.md) **:** `Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier (.*etl*) distinct. |


3. Attachez le profileur à l’application cible. Type :  

    **VSPerfCmd**  [/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [`Sample Event`]  

    `PID` spécifie l’ID de processus de l’application cible. `ProcessName` spécifie le nom du processus. Notez que si vous spécifiez `ProcessName` et que plusieurs processus de même nom sont en cours d’exécution, les résultats sont imprévisibles. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.  

    Par défaut, les données de performances sont échantillonnées tous les 10 000 000 cycles d’horloge ininterrompus du processeur. C’est-à-dire environ 100 fois par seconde sur un processeur de 1 GHz. Vous pouvez spécifier l’une des options suivantes pour modifier l’intervalle de cycle d’horloge ou spécifier un autre événement d’échantillonnage.  

   |Événement d'échantillon|Description|  
   |------------------|-----------------|  
   |[/timer](../profiling/timer.md) **:** `Interval`|Remplace l’intervalle d’échantillonnage par le nombre de cycles d’horloge ininterrompus spécifiés par `Interval`.|  
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Remplace l’événement d’échantillonnage par les erreurs de page. Si `Interval` est spécifié, définit le nombre d’erreurs de page entre chaque échantillon. La valeur par défaut est 10.|  
   |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Remplace l’événement d’échantillonnage par des appels système du processus vers le noyau du système d’exploitation (syscalls). Si `Interval` est spécifié, définit le nombre d’appels entre chaque échantillon. La valeur par défaut est 10.|  
   |[/counter](../profiling/counter.md) **:** `Config`|Remplace l’événement et l’intervalle d’échantillonnage par le compteur de performances du processeur et l’intervalle spécifié dans `Config`.|  

## <a name="control-data-collection"></a>Contrôler la collecte des données  
 Pendant l’exécution de l’application cible, vous pouvez utiliser les options de *VSPerfCmd.exe* pour démarrer et arrêter l’écriture des données dans le fichier de données du profileur. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.  

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données  

-   Les paires d’options **VSPerfCmd** suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  

    |Option|Description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par `PID`.|  
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach** commence à collecter des données pour le processus spécifié par `PID`. **/detach** arrête la collecte des données pour tous les processus.|  

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage  
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché à un processus profilé et doit être arrêté explicitement. Vous pouvez détacher le profileur d’une application profilée avec la méthode d’échantillonnage en fermant l’application ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /off** efface les variables d’environnement de profilage.  

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage  

1.  Effectuez l’une des opérations suivantes pour détacher le profileur de l’application cible.  

    -   Tapez **VSPerfCmd /detach**  

         - ou -  

    -   Fermez l’application cible.  

2.  Fermez le profileur. Type :  

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  

3.  (Facultatif) Effacez les variables d’environnement de profilage. Type :  

     **VSPerfClrEnv /off**  

## <a name="see-also"></a>Voir aussi  
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)