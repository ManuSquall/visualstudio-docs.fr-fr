---
title: 'Procédure : instrumenter un service .NET et collecter des données chronologiques détaillées en utilisant la ligne de commande du profileur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9f73593a-69a7-41b7-a21c-81d3ab0eb8fe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7931341080fbb2d2a98b695e5a864365c7bf6784
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766430"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Procédure : Instrumenter un service .NET et collecter des données de temporisation détaillées en utilisant la ligne de commande du profileur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] pour instrumenter un service [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] et pour collecter des données chronologiques détaillées.  

> [!NOTE]
>  Vous ne pouvez pas profiler un service avec la méthode d’instrumentation si le service ne peut pas être redémarré après le démarrage de l’ordinateur, comme un service qui démarre seulement quand le système d’exploitation démarre.  
>   
>  Les outils en ligne de commande des outils de profilage se trouvent dans le sous-répertoire \Team Tools\Performance Tools du répertoire d’installation de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande. Pour plus d’informations, consultez [Spécification du chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Pour ajouter des données d’interaction de couche à une exécution de profilage, vous devez utiliser des procédures spécifiques avec les outils de profilage en ligne de commande. Consultez [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 Pour collecter des données chronologiques détaillées à partir d’un service [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] avec la méthode d’instrumentation, utilisez l’outil [VSInstr.exe](../profiling/vsinstr.md) pour générer une version instrumentée du composant. Vous remplacez ensuite la version non instrumentée du service par la version instrumentée, en vérifiant que le service est configuré pour démarrer manuellement. Vous utilisez l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement de profilage globales, puis vous redémarrez l’ordinateur hôte. Vous démarrez ensuite le profileur.  

 Quand le service est démarré, les données chronologiques sont collectées automatiquement dans un fichier de données. Vous pouvez suspendre et reprendre la collecte des données pendant la session de profilage.  

 Pour mettre fin à une session de profilage, vous désactivez le service, puis vous arrêtez explicitement le profileur. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.  

## <a name="starting-the-application-with-the-profiler"></a>Démarrage de l’application avec le profileur  

#### <a name="to-start-profiling-a-net-framework-service"></a>Pour démarrer le profilage d’un service .NET Framework  

1. Ouvrez une fenêtre d’invite de commandes.  

2. Utilisez l’outil **VSInstr** pour générer une version instrumentée du fichier binaire du service.  

3. Remplacez le fichier binaire d’origine par la version instrumentée. Dans le Gestionnaire de contrôle des services Windows, vérifiez que le type de démarrage du service est défini sur Manuel.  

4. Initialisez les variables d’environnement de profilage [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Type :  

    **VSPerfClrEnv /globaltraceon**  

5. Redémarrez l'ordinateur.  

6. Ouvrez une fenêtre d’invite de commandes.  

7. Démarrez le profileur. Type :  

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  

   - L’option [/start](../profiling/start.md)**:trace** initialise le profileur.  

   - L’option [/output](../profiling/output.md)**:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).  

     Vous pouvez utiliser une des options suivantes avec l’option **/start:trace**.  

   > [!NOTE]
   >  Les options **/user** et **/crosssession** sont généralement nécessaires pour le profilage des services.  

   |                                 Option                                  |                                                                                                                                            Description                                                                                                                                             |
   |-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |        Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows.         |
   |              [/crosssession](../profiling/crosssession.md)              | Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si l’application s’exécute dans une autre session. L’ID de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   |        [/waitstart](../profiling/waitstart.md)[**:**`Interval`]         |                                          Spécifie le nombre de secondes à attendre que le profileur s’initialise avant qu’il retourne une erreur. Si `Interval` n’est pas spécifié, le profileur attend indéfiniment. Par défaut, **/start** retourne immédiatement.                                           |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                      Pour démarrer le profileur après avoir suspendu la collecte de données, ajoutez l’option **/globaloff** sur la ligne de commande **/start**. Utilisez **/globalon** pour reprendre le profilage.                                                                       |
   |           [/counter](../profiling/counter.md) **:** `Config`            |                                                                    Collecte des informations du compteur de performances du processeur spécifié dans la configuration. Les informations du compteur sont ajoutées aux données collectées à chaque événement de profilage.                                                                    |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                             Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage.                                                                                                              |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                           À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms.                                                                            |
   |       [/events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                              Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl).                                                                              |


8. Démarrez le service à partir du Gestionnaire de contrôle des services Windows.  

## <a name="controlling-data-collection"></a>Contrôle de la collection de données  
 Quand le service s’exécute, vous pouvez utiliser les options de **VSPerfCmd.exe** pour démarrer et arrêter l’écriture des données dans le fichier de données du profileur. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, comme le démarrage ou l’arrêt du service.  

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données  

-   Les paires d’options **VSPerfCmd** suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  

    |Option|Description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|  

## <a name="ending-the-profiling-session"></a>Fin d’une session de profilage  
 Pour mettre fin à une session de profilage, arrêtez le service qui exécute le composant instrumenté, puis appelez l’option **VSPerfCmd**[/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement du profilage.  

 Vous devez redémarrer l’ordinateur pour que les nouveaux paramètres d’environnement soient appliqués.  

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage  

1.  Arrêtez le service à partir du Gestionnaire de contrôle des services.  

2.  Fermez le profileur. Type :  

     **VSPerfCmd /shutdown**  

3.  Quand vous avez terminé le profilage, effacez les variables d’environnement de profilage. Type :  

     **VSPerfClrEnv /globaloff**  

4.  Remplacez le module instrumenté par l’original. Si nécessaire, reconfigurez le type de démarrage du service.  

5.  Redémarrez l'ordinateur.  

## <a name="see-also"></a>Voir aussi  
 [Profilage de services](../profiling/command-line-profiling-of-services.md)   
 [Vues de données de la méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)
