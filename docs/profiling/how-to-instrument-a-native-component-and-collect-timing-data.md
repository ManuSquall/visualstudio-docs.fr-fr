---
title: Ligne de commande du profileur-instrumentation Native Component, recevoir des données de minutage
description: Découvrez comment utiliser les outils en ligne de commande Outils de profilage Visual Studio pour collecter des données de temporisation détaillées pour un composant natif, tel qu’un fichier. exe ou. dll C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 7d63ec7bded9cc19e31ee0d6f8ce7346990bf7aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929132"
---
# <a name="how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Guide pratique pour instrumenter un composant autonome natif et collecter les données temporelles avec le profileur à partir de la ligne de commande
Cette rubrique explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour instrumenter un composant natif comme un fichier .*exe* ou .*dll* C++, et pour collecter des données chronologiques détaillées.

> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

Pour collecter des données chronologiques détaillées à partir d’un composant avec la méthode d’instrumentation, vous utilisez l’outil [VSInstr.exe](../profiling/vsinstr.md) pour générer une version instrumentée du composant. Vous démarrez ensuite le profileur. Quand le composant instrumenté est exécuté, les données chronologiques sont collectées automatiquement dans un fichier de données. Vous pouvez suspendre et reprendre la collecte des données pendant la session de profilage.

 Pour mettre fin à une session de profilage, fermez l’application cible, puis arrêtez explicitement le profileur.

## <a name="start-the-profiling-session"></a>Démarrer la session de profilage

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Pour démarrer le profilage avec la méthode d’instrumentation

1. Ouvrez une fenêtre d’invite de commandes.

2. Utilisez l’outil **VSInstr** pour générer une version instrumentée de l’application cible.

3. Démarrez le profileur. Tapez :

    **VSPerfCmd/start : trace/output :** `OutputFile` [`Options`]

   - L’option [/start](../profiling/start.md)**:trace** initialise le profileur.

   - L’option [/Output](../profiling/output.md)**:** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser une ou plusieurs des options suivantes avec l’option **/start:trace**.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est listé dans la colonne **nom d’utilisateur** sous l’onglet **processus** du gestionnaire des tâches de Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si l’application s’exécute dans une autre session. L’identificateur de session est indiqué dans la colonne **ID de session** sous l’onglet processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Démarre le profileur avec la collecte de données suspendue. Utilisez [/globalon](../profiling/globalon-and-globaloff.md) pour reprendre le profilage. |
   | [/Counter](../profiling/counter.md) **:**`Config` | Collecte des informations à partir du compteur de performances du processeur spécifié dans `Config`. Les informations du compteur sont ajoutées aux données collectées à chaque événement de profilage. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un (.*fichier ETL*). |

4. Démarrez l’application cible de manière habituelle.

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour mettre fin à une session de profilage, fermez l’application qui exécute le composant instrumenté, puis appelez l’option de **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Fermez l’application cible.

2. Fermez le profileur. Tapez :

     **VSPerfCmd /shutdown**

## <a name="see-also"></a>Voir aussi
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Vues de données de la méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)
