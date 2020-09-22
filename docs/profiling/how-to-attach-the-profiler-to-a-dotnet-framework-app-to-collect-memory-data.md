---
title: Attacher le profileur à .NET pour collecter des données de mémoire
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 88b3eedf8989b4c7421ecb7504b18997058a0204
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811108"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Guide pratique pour attacher le profileur à une application .NET Framework autonome et collecter des données de mémoire en utilisant la ligne de commande

Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage Visual Studio pour attacher le profileur à une application .NET Framework autonome (cliente) en cours d’exécution et collecter des données de mémoire.

> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

Pour attacher une application .NET Framework et collecter des données de mémoire, vous devez utiliser l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement appropriées avant le démarrage de l’application cible. Quand le profileur est attaché à l’application, vous pouvez utiliser l’outil *VSPerfCmd.exe* pour suspendre et reprendre la collecte des données.

Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché à un processus profilé et doit être arrêté explicitement. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.

## <a name="attach-the-profiler"></a>Attacher le profileur

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Pour attacher le profileur à une application .NET Framework en cours d’exécution

1. Ouvrez une fenêtre d’invite de commandes.

2. Initialisez les variables d’environnement de profilage. Tapez :

     **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - Les options **/samplegc** et **/samplegclife** spécifient s’il faut collecter seulement les données d’allocation de mémoire, ou collecter à la fois les données d’allocation de mémoire et les données de durée de vie des objets. Vous ne pouvez spécifier qu’une seule option.

        |Option|Descriptions|
        |------------|------------------|
        |**/samplegc**|Collecter seulement les données d’allocation de mémoire.|
        |**/samplegclife**|Collecte à la fois les données d’allocation de mémoire et les données de durée de vie des objets.|

    - L’option **/samplelineoff** désactive la collecte des données de ligne de code source.

3. Démarrez le profileur. Tapez :

     **VSPerfCmd/start : exemple/output :** `OutputFile` [`Options`]

   - L’option [/start](../profiling/start.md)**:sample** initialise le profileur.

   - L’option [/Output](../profiling/output.md)**:** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:sample**.

     | Option | Description |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows. |
     | [/crosssession &#124; /cs](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si l’application s’exécute dans une autre session. L’identificateur de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
     | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
     | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |

4. Si nécessaire, démarrez l’application cible de la façon habituelle.

5. Attachez le profileur à l’application cible. Tapez :

     **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/TargetCLR](../profiling/targetclr.md)**:** `Version` ]  

    - `PID` spécifie l’ID de processus de l’application cible. `ProcessName` spécifie le nom du processus. Notez que si vous spécifiez `ProcessName` et que plusieurs processus de même nom sont en cours d’exécution, les résultats sont imprévisibles. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.

    - **/TargetCLR :** `Version` spécifie la version du common language runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application. Optionnel.

## <a name="control-data-collection"></a>Contrôler la collecte des données

Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par le `PID`.|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach** démarre la collecte de données pour le processus spécifié par le `PID` ou par le nom du processus (ProcName). **/Detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus spécifique n’est spécifié.|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage

Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché à un processus profilé et doit être arrêté explicitement. Vous pouvez détacher le profileur d’une application profilée avec la méthode d’échantillonnage en fermant l’application ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /off** efface les variables d’environnement de profilage.

### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Effectuez l’une des opérations suivantes pour détacher le profileur de l’application cible :

    - Tapez **VSPerfCmd/detach**

         - ou -

    - Fermez l’application cible.

2. Fermez le profileur. Tapez :

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

3. (Facultatif) Effacez les variables d’environnement de profilage. Tapez :

     **VSPerfCmd /off**

## <a name="see-also"></a>Voir aussi

[Profiler des applications](../profiling/command-line-profiling-of-stand-alone-applications.md) 
 autonomes [Vues de données de mémoire .net](../profiling/dotnet-memory-data-views.md)
