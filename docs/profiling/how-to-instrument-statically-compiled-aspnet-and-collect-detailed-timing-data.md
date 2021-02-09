---
title: Ligne de commande du profileur-instrumenter une application ASP.NET statique, recevoir des données de minutage
description: Découvrez comment utiliser les outils en ligne de commande Outils de profilage Visual Studio pour collecter des données de temporisation détaillées pour un composant Web ou un site Web ASP.NET précompilé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 65db2ebe3b79fbe1391e59c9e948dc8cb034a57c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929002"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Guide pratique pour instrumenter une application web ASP.NET compilée statiquement et collecter des données temporelles détaillées avec le profileur en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour instrumenter un site web ou un composant web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] précompilé et pour collecter des données chronologiques détaillées.

> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.
>
> L’ajout de données d’interaction de couche à une exécution de profilage nécessite des procédures spécifiques avec les outils de profilage en ligne de commande. Consultez [collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Pour collecter des données chronologiques détaillées à partir d’un composant web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] avec la méthode d’instrumentation, vous utilisez l’outil [VSInstr.exe](../profiling/vsinstr.md) pour générer une version instrumentée du composant. Sur l’ordinateur qui héberge le composant, vous remplacez la version non instrumentée du composant par la version instrumentée. Vous utilisez ensuite l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement de profilage globales et redémarrer l’ordinateur hôte. Vous démarrez ensuite le profileur.

 Quand le composant instrumenté est exécuté, les données chronologiques sont collectées automatiquement dans un fichier de données. Vous pouvez suspendre et reprendre la collecte des données pendant la session de profilage.

 Pour mettre fin à une session de profilage, vous fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui héberge le composant, puis vous arrêtez explicitement le profileur. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.

## <a name="start-to-profile"></a>Commencer à profiler

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Pour instrumenter un composant web ASP.NET et démarrer le profilage

1. Ouvrez une fenêtre d’invite de commandes.

2. Utilisez l’outil **VSInstr** pour générer une version instrumentée de l’application cible. Si nécessaire, remplacez les fichiers binaires de l’application sur l’ordinateur hôte ASP.NET avec les fichiers binaires instrumentés.

3. Initialisez les variables d’environnement du profilage .NET. Dans la fenêtre Invite de commandes, tapez :

    **VSPerfClrEnv /globaltraceon**

4. Redémarrez l'ordinateur.

5. Ouvrez une fenêtre d’invite de commandes. Si nécessaire, définissez le chemin d’accès des outils du profileur.

6. Démarrez le profileur. Tapez :

    **VSPerfCmd/start : trace/output :** `OutputFile` [`Options`]

   - L’option [/start](../profiling/start.md)**:trace** initialise le profileur.

   - L’option [/Output](../profiling/output.md)**:** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:trace**.

   > [!NOTE]
   > Les options **/user** et **/crosssession** sont généralement nécessaires pour les applications ASP.NET.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus de travail ASP.NET. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que l’utilisateur connecté. Le propriétaire du processus est listé dans la colonne **nom d’utilisateur** sous l’onglet **processus** du gestionnaire des tâches de Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’identificateur de session est indiqué dans la colonne ID de session sous l’onglet **processus** du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un (.*fichier ETL*). |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Pour démarrer le profileur après avoir suspendu la collecte de données, ajoutez l’option **/globaloff** sur la ligne de commande **/start**. Utilisez **/globalon** pour reprendre le profilage. |

7. Ouvrez le site web qui contient le composant instrumenté.

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
 Pour mettre fin à une session de profilage, fermez l' [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application Web, puis utilisez la commande Internet Information Services (IIS) **IISReset** pour fermer le [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processus de travail. Appelez l’option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage.

 La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement du profilage. Vous devez redémarrer l’ordinateur pour que les nouveaux paramètres d’environnement soient appliqués.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Tapez :

    **IISReset /stop**

3. Fermez le profileur. Tapez :

    **VSPerfCmd /shutdown**

4. (Facultatif). Effacez les variables d’environnement de profilage. Tapez :

    **VSPerfCmd /globaloff**

5. Redémarrez l'ordinateur.

## <a name="see-also"></a>Voir aussi
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Vues de données de la méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)
