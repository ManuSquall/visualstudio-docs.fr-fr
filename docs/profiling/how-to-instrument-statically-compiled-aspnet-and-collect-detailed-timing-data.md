---
title: Guide pratique pour instrumenter une application Web ASP.NET compilée statiquement et collecter des données de temporisation détaillées avec le profileur en utilisant la ligne de commande │Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: efb4e449114a0920c5fd73feba10b1e0d9e0be3a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865405"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Guide pratique pour instrumenter une application web ASP.NET compilée statiquement et collecter des données temporelles détaillées avec le profileur en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour instrumenter un site web ou un composant web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] précompilé et pour collecter des données chronologiques détaillées.  

> [!NOTE]
>  Les outils en ligne de commande des Outils de profilage se trouvent dans le sous-répertoire *\Team Tools\Performance Tools* du répertoire d’installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande. Pour plus d’informations, consultez [Spécifier le chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
> 
>  Pour ajouter des données d’interaction de couche à une exécution de profilage, vous devez utiliser des procédures spécifiques avec les outils de profilage en ligne de commande. Consultez [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 Pour collecter des données chronologiques détaillées à partir d’un composant web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] avec la méthode d’instrumentation, vous utilisez l’outil [VSInstr.exe](../profiling/vsinstr.md) pour générer une version instrumentée du composant. Sur l’ordinateur qui héberge le composant, vous remplacez la version non instrumentée du composant par la version instrumentée. Vous utilisez ensuite l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement de profilage globales et redémarrer l’ordinateur hôte. Vous démarrez ensuite le profileur.  

 Quand le composant instrumenté est exécuté, les données chronologiques sont collectées automatiquement dans un fichier de données. Vous pouvez suspendre et reprendre la collecte des données pendant la session de profilage.  

 Pour mettre fin à une session de profilage, vous fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui héberge le composant, puis vous arrêtez explicitement le profileur. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.  

## <a name="start-to-profile"></a>Commencer à profiler  

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Pour instrumenter un composant web ASP.NET et démarrer le profilage  

1. Ouvrez une fenêtre Invite de commandes.  

2. Utilisez l’outil **VSInstr** pour générer une version instrumentée de l’application cible. Si nécessaire, remplacez les fichiers binaires de l’application sur l’ordinateur hôte ASP.NET avec les fichiers binaires instrumentés.  

3. Initialisez les variables d’environnement du profilage .NET. Dans la fenêtre Invite de commandes, tapez :  

    **VSPerfClrEnv /globaltraceon**  

4. Redémarrez l'ordinateur.  

5. Ouvrez une fenêtre Invite de commandes. Si nécessaire, définissez le chemin d’accès des outils du profileur.  

6. Démarrez le profileur. Type :  

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  

   - L’option [/start](../profiling/start.md)**:trace** initialise le profileur.  

   - L’option [/output](../profiling/output.md)**:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).  

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:trace**.  

   > [!NOTE]
   >  Les options **/user** et **/crosssession** sont généralement nécessaires pour les applications ASP.NET.  

   | Option | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus de travail ASP.NET. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que l’utilisateur connecté. Le propriétaire de processus est listé dans la colonne **Nom d’utilisateur**, sous l’onglet **Processus** du Gestionnaire des tâches Windows. |
   | [/crosssession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’identificateur de session est répertorié dans la colonne ID de session, sous l’onglet **Processus** du Gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/automark](../profiling/automark.md) **:** `Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier (.*etl*) distinct. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Pour démarrer le profileur après avoir suspendu la collecte de données, ajoutez l’option **/globaloff** sur la ligne de commande **/start**. Utilisez **/globalon** pour reprendre le profilage. |


7. Ouvrez le site web qui contient le composant instrumenté.  

## <a name="control-data-collection"></a>Contrôler la collecte des données  
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.  

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données  

-   Les paires d’options suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  

    |Option|Description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|  

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage  
 Pour terminer une session de profilage, fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], puis utilisez la commande **IISReset** d’Internet Information Services (IIS) pour fermer le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Appelez l’option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage.  

 La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement du profilage. Vous devez redémarrer l’ordinateur pour que les nouveaux paramètres d’environnement soient appliqués.  

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage  

1. Fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  

2. Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Type :  

    **IISReset /stop**  

3. Fermez le profileur. Type :  

    **VSPerfCmd /shutdown**  

4. (Facultatif). Effacez les variables d’environnement de profilage. Type :  

    **VSPerfCmd /globaloff**  

5. Redémarrez l'ordinateur.  

## <a name="see-also"></a>Voir aussi  
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vues de données de la méthode d'instrumentation](../profiling/instrumentation-method-data-views.md)