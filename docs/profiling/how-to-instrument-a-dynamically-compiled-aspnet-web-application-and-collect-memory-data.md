---
title: 'Procédure : Instrumenter une application web ASP.NET compilée dynamiquement et collecter des données de mémoire avec le profileur en ligne de commande | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 172f4a367aa520ebd0fac62d25007713c47e5801
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386279"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Procédure : Instrumenter une application web ASP.NET compilée dynamiquement et collecter des données de mémoire avec le profileur en ligne de commande
Cette rubrique explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] afin de collecter des données détaillées sur l’allocation de mémoire et la durée de vie des objets dans .NET pour une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilée dynamiquement à l’aide de la méthode de profilage par instrumentation.

> [!NOTE]
> Pour obtenir le chemin d’accès des outils de profilage, voir [Spécifier le chemin d’accès des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

 Pour collecter les données de performances d’une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], modifiez le fichier *web.config* de l’application cible pour permettre à l’outil [VSInstr.exe](../profiling/vsinstr.md) d’instrumenter les fichiers d’application compilés dynamiquement. Utilisez ensuite l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour configurer le serveur qui héberge l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et activer le profilage de mémoire .NET en définissant les variables d’environnement appropriées, puis redémarrez l’ordinateur.

 Pour collecter des données, démarrez Profiler, puis exécutez l’application cible. Pendant que Profiler est attaché à l’application, vous pouvez mettre en pause et reprendre la collecte des données. Une fois que vous avez collecté les données appropriées, fermez l’application, fermez le processus de travail IIS (Internet Information Services), puis arrêtez Profiler.

 Une fois que vous avez terminé votre travail de profilage, restaurez le fichier *web.config* et le serveur web à leur état d’origine.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Pour configurer l’application web ASP.NET et le serveur web

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Pour configurer l’application web ASP.NET et le serveur web

1. Modifiez le fichier *web.config* de l’application cible. Voir [Guide pratique pour modifier des fichiers web.config pour instrumenter et profiler des applications web ASP.NET compilées dynamiquement](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Ouvrez une fenêtre d’invite de commandes sur l’ordinateur qui héberge l’application web.

3. Initialisez les variables d’environnement de profilage. Type :

     **VSPerfClrEnv /globaltracegc**

     - ou -

     **VSPerfClrEnv /globaltracegclife**

    - **/globaltracegc** permet d’activer la collecte des données d’allocation de mémoire.

    - **/globaltracegclife** permet d’activer la collecte des données d’allocation de mémoire et des données de durée de vie des objets.

4. Redémarrez l'ordinateur.

## <a name="run-the-profiling-session"></a>Exécuter la session de profilage

#### <a name="to-profile-the-aspnet-web-application"></a>Pour profiler l’application web ASP.NET

1. Démarrez le profileur. Type :

    **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - L’option **/start:trace** initialise le profileur.

   - L’option **/output:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données de profilage (.*vsp*).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:trace**.

   > [!NOTE]
   > Les options **/user** et **/crosssession** sont généralement nécessaires pour les applications ASP.NET.

   | Option | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Spécifie les informations facultatives relatives au nom de domaine et au nom d’utilisateur du compte propriétaire du processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que l’utilisateur connecté. Le nom est répertorié dans la colonne **Nom d’utilisateur**, sous l’onglet **Processus** du Gestionnaire des tâches de Windows. |
   | [/crosssession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si l’application s’exécute dans une autre session. L’ID de session est répertorié dans la colonne **ID de session**, sous l’onglet **Processus** du Gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Démarre le profileur avec la collecte de données suspendue. Utilisez [/globalon](../profiling/globalon-and-globaloff.md) pour reprendre le profilage. |
   | [/counter](../profiling/counter.md) **:** `Config` | Collecte les informations du compteur de performances du processeur spécifié dans `Config`. Les informations du compteur sont ajoutées aux données collectées à chaque événement de profilage. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/automark](../profiling/automark.md) **:** `Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier (.*etl*) distinct. |

2. Démarrez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de manière habituelle.

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier de données du profileur à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|

- Vous pouvez également utiliser l’option **VSPerfCmd.exe**[/mark](../profiling/mark.md) pour insérer une marque de profilage dans le fichier de données. La commande **/mark** ajoute un identificateur, un horodatage et une chaîne de caractères facultative définie par l’utilisateur. Les marques peuvent être utilisées pour filtrer les données des rapports et des vues de données du profileur.

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour mettre fin à une session de profilage, fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] cible, arrêtez IIS (Internet Information Services) pour arrêter le processus profilé, puis arrêtez Profiler. Redémarrez ensuite IIS.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en réinitialisant Internet Information Services (IIS). Type :

    **IISReset /stop**

3. Fermez le profileur. Type :

    **VSPerfCmd** [/shutdown](../profiling/shutdown.md)

4. Redémarrez IIS. Type :

    **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>Restaurer la configuration de l’application et de l’ordinateur
 Une fois que vous avez effectué l’ensemble du profilage, remplacez le fichier *web.config*, effacez les variables d’environnement de profilage, puis redémarrez l’ordinateur pour restaurer l’état d’origine du serveur et de l’application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

#### <a name="to-restore-the-application-and-computer-configuration"></a>Pour restaurer la configuration de l’application et de l’ordinateur

1. Remplacez le fichier *web.config* par une copie du fichier d’origine.

2. (Facultatif). Effacez les variables d’environnement de profilage. Type :

     **VSPerfCmd /globaloff**

3. Redémarrez l'ordinateur.

## <a name="see-also"></a>Voir aussi
- [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Vues des données de la mémoire .NET](../profiling/dotnet-memory-data-views.md)
