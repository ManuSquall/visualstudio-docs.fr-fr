---
title: Guide pratique pour instrumenter une application Web ASP.NET compilée dynamiquement et collecter des données de temporisation détaillées avec le profileur en utilisant la ligne de commande │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7c1f3073b1b3ebeb142805e5d34097c82e038e67
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Comment : instrumenter une application Web ASP.NET compilée dynamiquement et collecter des données de temporisation détaillées avec le profileur en utilisant la ligne de commande

Cette rubrique explique comment utiliser les outils en ligne de commande des Outils de profilage Visual Studio afin de collecter des données de temporisation détaillées pour une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilée dynamiquement via la méthode de profilage par instrumentation.

> [!NOTE]
> Les outils en ligne de commande des outils de profilage se trouvent dans le sous-répertoire \Team Tools\Performance Tools du répertoire d’installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande. Pour plus d’informations, consultez [Spécification du chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

Pour collecter les données de performances d’une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous modifiez le fichier web.config de l’application cible pour permettre à l’outil [VSInstr.exe](../profiling/vsinstr.md) d’instrumenter les fichiers d’application compilés dynamiquement. Vous utilisez ensuite l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour définir les variables d’environnement appropriées sur le serveur web afin d’activer le profilage, puis redémarrez l’ordinateur.

Démarrez le profileur, puis exécutez l’application cible. Lorsque le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte de données. Une fois le profilage terminé, fermez l’application, fermez le processus de travail Internet Information Services (IIS), puis arrêtez le profileur. Une fois que vous avez terminé votre travail de profilage, restaurez le fichier web.config et le serveur web à leur état d’origine.

## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Configuration de l’application web ASP.NET et du serveur web

1. Modifiez le fichier web.config de l’application cible. Consultez [Guide pratique pour modifier des fichiers web.config pour instrumenter et profiler des applications web ASP.NET compilées dynamiquement](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md).

2. Ouvrez une fenêtre Invite de commandes.

3. Initialisez les variables d’environnement de profilage. Type :

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** permet le profilage à l’aide de la méthode d’instrumentation.

4. Redémarrez l'ordinateur.

## <a name="running-the-profiling-session"></a>Exécution de la session de profilage

1. Ouvrez une fenêtre Invite de commandes.

2. Démarrez le profileur. Type :

     **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

    - L’option **/start:trace** initialise le profileur.

    - L’option **/output:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:trace**.

    > [!NOTE]
    > Les options **/user** et **/crosssession** sont généralement nécessaires pour les applications ASP.NET.

    |Option|Description|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus de travail ASP.NET. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows.|
    |[/crosssession](../profiling/crosssession.md)|Active le profilage des processus dans d’autres sessions ouvertes. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’identificateur de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**.|
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Démarre le profileur avec la collecte de données suspendue. Utilisez [/globalon](../profiling/globalon-and-globaloff.md) pour reprendre le profilage.|
    |[/counter](../profiling/counter.md) **:** `Config`|Collecte des informations à partir du compteur de performances du processeur spécifié dans `Config`. Les informations du compteur sont ajoutées aux données collectées à chaque événement de profilage.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage.|
    |[/automark](../profiling/automark.md) **:** `Interval`|À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl).|

3. Démarrez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de manière habituelle.

## <a name="controlling-data-collection"></a>Le contrôle de la collecte de données

Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier de données du profileur à l’aide des options de **VSPerfCmd.exe**. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

- Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|

- Vous pouvez également utiliser l’option **VSPerfCmd.exe**[/mark](../profiling/mark.md) pour insérer une marque de profilage dans le fichier de données. La commande **/mark** ajoute un identificateur, un horodatage et une chaîne de texte facultative définie par l’utilisateur. Les marques peuvent être utilisées pour filtrer les données des rapports et des vues de données du profileur.

## <a name="ending-the-profiling-session"></a>La fin de la session de profilage

Pour terminer une session de profilage, fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] cible, réinitialisez IIS pour arrêter le processus profilé, puis arrêtez le profileur.

1. Fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en réinitialisant Internet Information Services (IIS). Type :

     **IISReset /stop**

3. Fermez le profileur. Type :

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

4. Redémarrez IIS. Type :

     **IISReset /start**

## <a name="restoring-the-application-and-computer-configuration"></a>Restauration de la configuration de l’application et de l’ordinateur

Une fois que vous avez terminé tout le profilage, remplacez le fichier web.config, effacez les variables d’environnement de profilage et redémarrez l’ordinateur pour restaurer l’état d’origine (avant le profilage) de l’application et du serveur.

1. Remplacez le fichier web.config par une copie du fichier d’origine.

2. Effacez les variables d’environnement de profilage. Type :

     **VSPerfCmd /globaloff**

3. Redémarrez l'ordinateur.

## <a name="see-also"></a>Voir aussi

[Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
[Vues de données de la méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)