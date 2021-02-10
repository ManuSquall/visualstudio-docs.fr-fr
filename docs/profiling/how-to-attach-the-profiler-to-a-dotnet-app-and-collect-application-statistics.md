---
title: Attacher le profileur à l’application autonome .NET ; Obtient les statistiques de l’application
description: Apprenez à utiliser les outils en ligne de commande de Visual Studio Outils de profilage pour attacher le profileur à une application en cours d’exécution .NET Framework autonome (client) et obtenir des statistiques.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 52a1e52590073c48f0386c5d174eec8193f1518d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958919"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Guide pratique pour attacher le profileur à une application .NET Framework autonome et collecter des statistiques d’application en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à une application .NET Framework autonome (cliente) en cours d’exécution et collecter des statistiques de performances à l’aide de la méthode d’échantillonnage.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.
>
> L’ajout de données d’interaction de couche à une exécution de profilage nécessite des procédures spécifiques avec les outils de profilage en ligne de commande. Consultez [Collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Pour collecter les données de performances à partir d’une application .NET Framework, les variables d’environnement appropriées doivent être initialisées avant le démarrage de l’application cible. Quand le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte des données.

 Pour terminer une session de profilage, le profileur ne doit plus être attaché à l’application et doit être arrêté explicitement. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session de profilage.

## <a name="attach-the-profiler"></a>Attacher le profileur

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Pour attacher le profileur à une application .NET Framework en cours d’exécution

1. Ouvrez une fenêtre d’invite de commandes.

2. Initialisez les variables d’environnement de profilage. Tapez :

    **VSPerfClrEnv /sampleon** [**/samplelineoff**]

   - L’option **/samplelineoff** désactive la collecte des données de ligne de code source.

3. Démarrez le profileur. Tapez :

    **VSPerfCmd/start : exemple/output :** `OutputFile` [`Options`]

   - L’option [/start](../profiling/start.md)**:sample** initialise le profileur.

   - L’option [/Output](../profiling/output.md)**:** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser une des options suivantes avec l’option **/start:sample**.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur facultatif du compte propriétaire du processus profilé. Cette option n’est nécessaire que si l’application profilée a été démarrée sous le compte d’un utilisateur autre que celui connecté. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. **/CS** peut être spécifié comme abréviation de **/crosssession**. Cette option est nécessaire si l’application s’exécute dans une autre session. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un (.*fichier ETL*). |

4. Si nécessaire, démarrez l’application cible de la façon habituelle.

5. Attachez le profileur à l’application cible. Tapez :

    **VSPerfCmd/Attach :**{ `PID`&#124;`ProcessName` } [ `Sample Event` ] [**/TargetCLR :** `Version` ]

   - `PID` spécifie l’ID de processus de l’application cible. `ProcessName` spécifie le nom du processus. Notez que si vous spécifiez `ProcessName` et que plusieurs processus de même nom sont en cours d’exécution, les résultats sont imprévisibles. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.

   - [/TargetCLR](../profiling/targetclr.md) **:** `Version` spécifie la version du Common Language Runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application. Facultatif.

   - Par défaut, les données de performances sont échantillonnées tous les 10 000 000 cycles d’horloge ininterrompus du processeur. Cela correspond environ à une fois toutes les 10 secondes sur un processeur de 1 GH. Vous pouvez spécifier l’une des options suivantes pour modifier l’intervalle de cycle d’horloge ou pour spécifier un autre événement d’échantillonnage. [/TargetCLR](../profiling/targetclr.md)**:** `Version` spécifie la version du CLR à profiler lorsque plusieurs versions du runtime sont chargées dans une application. Facultatif.

   |Exemple d’événement|Description|
   |-|-|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Remplace l’intervalle d’échantillonnage par le nombre de cycles d’horloge ininterrompus spécifiés par `Interval`.|
   |[/PF](../profiling/pf.md) [**:** `Interval` ]|Remplace l’événement d’échantillonnage par les erreurs de page. Si `Interval` est spécifié, définit le nombre d’erreurs de page entre chaque échantillon. La valeur par défaut est 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Remplace l’événement d’échantillonnage par des appels système du processus vers le noyau du système d’exploitation (syscalls). Si `Interval` est spécifié, définit le nombre d’appels entre chaque échantillon. La valeur par défaut est 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Remplace l’événement et l’intervalle d’échantillonnage par le compteur de performances du processeur et l’intervalle spécifié dans `Config`.|

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier de données du profileur à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par le `PID`.|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach** démarre la collecte de données pour le processus spécifié par le `PID` ou par le nom du processus (ProcName). **/Detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus spécifique n’est spécifié.|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché à un processus profilé et doit être arrêté explicitement. Vous pouvez détacher le profileur d’une application profilée avec la méthode d’échantillonnage en fermant l’application ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /off** efface les variables d’environnement de profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Effectuez l’une des opérations suivantes pour détacher le profileur de l’application cible :

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
