---
title: Attacher le profileur à une application .NET pour collecter des données de mémoire
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 04dcf800074476b285a07e36db5a85fa3a366585
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779127"
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

     **VSPerfCmd /start:sample /output:** `OutputFile` [ ]`Options`

   - L’option [/start](../profiling/start.md)**:sample** initialise le profileur.

   - La [/sortie](../profiling/output.md)**:** `OutputFile` option est requise avec **/démarrer**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:sample**.

     | Option | Description |
     | - | - |
     | [/utilisateur](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows. |
     | [/crosssession &#124; /cs](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si l’application s’exécute dans une autre session. L’identificateur de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
     | [/automark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |

4. Si nécessaire, démarrez l’application cible de la façon habituelle.

5. Attachez le profileur à l’application cible. Tapez :

     **VSPerfCmd**[/attach](../profiling/attach.md) **:**`PID`&#124;`ProcName`[[/targetclr](../profiling/targetclr.md)**:**`Version`]  

    - `PID` spécifie l’ID de processus de l’application cible. `ProcessName` spécifie le nom du processus. Notez que si vous spécifiez `ProcessName` et que plusieurs processus de même nom sont en cours d’exécution, les résultats sont imprévisibles. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.

    - **/targetclr:** `Version` spécifie la version de l’heure de l’exécution de la langue commune (CLR) au profil lorsque plus d’une version de l’exécution est chargée dans une application. facultatif.

## <a name="control-data-collection"></a>Contrôler la collecte des données

Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par le `PID`.|
    |[/attacher](../profiling/attach.md) **:**:`PID`&#124;`ProcName`'/détache '**' '** `ProcName`' ' ' ' ' '&#124;' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' [' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '](../profiling/detach.md)`PID`|**/attach** démarre la collecte de données pour le processus spécifié par le `PID` ou par le nom du processus (ProcName). **/détacher** arrête la collecte de données pour le processus spécifié ou pour tous les processus si un processus spécifique n’est pas spécifié.|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage

Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché à un processus profilé et doit être arrêté explicitement. Vous pouvez détacher le profileur d’une application profilée avec la méthode d’échantillonnage en fermant l’application ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /off** efface les variables d’environnement de profilage.

### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Effectuez l’une des opérations suivantes pour détacher le profileur de l’application cible :

    - Type **VSPerfCmd /detach**

         -ou-

    - Fermez l’application cible.

2. Fermez le profileur. Tapez :

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. (Facultatif) Effacez les variables d’environnement de profilage. Tapez :

     **VSPerfCmd /off**

## <a name="see-also"></a>Voir aussi

[Profil applications](../profiling/command-line-profiling-of-stand-alone-applications.md)
autonomes[.NET vues de données de mémoire](../profiling/dotnet-memory-data-views.md)
