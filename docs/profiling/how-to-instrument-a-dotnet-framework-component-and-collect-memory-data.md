---
title: 'Procédure : Instrumenter un composant .NET Framework autonome et collecter des données de mémoire avec le profileur en ligne de commande | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c9bed8b40e1ce601515a92f1f55a62d54cfb7d30
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917460"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Procédure : Instrumenter un composant .NET Framework autonome et collecter des données de mémoire avec le profileur en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour instrumenter un composant .NET Framework d’une application autonome, tel qu’un fichier .exe ou .dll, pour collecter des informations relatives à la mémoire à l’aide du profileur.  

> [!NOTE]
>  Pour obtenir le chemin d’accès des outils de profilage, voir [Spécifier le chemin d’accès des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.  


 Pour collecter les données de mémoire d’un composant .NET Framework à l’aide de la méthode d’instrumentation, utilisez l’outil [VSInstr.exe](../profiling/vsinstr.md) pour générer une version instrumentée du composant, et l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement de profilage. Ensuite, démarrez le profileur à l’aide de l’outil *VSPerfCmd.exe*.  

 Lorsque le composant instrumenté est exécuté, les données de mémoire sont automatiquement rassemblées dans un fichier de données. Vous pouvez suspendre et reprendre la collecte des données pendant la session de profilage.  

 Pour mettre fin à une session de profilage, fermez l’application cible et arrêtez explicitement le profileur. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.  

## <a name="start-the-application-with-the-profiler"></a>Démarrer l’application avec le profileur  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Pour attacher le profileur à une application .NET Framework en cours d’exécution  

1. Ouvrez une fenêtre Invite de commandes.  

2. Utilisez l’outil **VSInstr** pour générer une version instrumentée de l’application cible.  

3. Initialisez les variables d’environnement de profilage .NET Framework. Type :  

    **VSPerfClrEnv** {**/tracegc** &#124; **/tracegclife**}  

   -   Les options **/tracegc** et **/tracegclife** initialisent les variables d’environnement pour collecter uniquement des données d’allocation de mémoire, ou pour collecter à la fois des données d’allocation de mémoire et des données de durée de vie des objets.  

       |Option|Description|  
       |------------|-----------------|  
       |**/tracegc**|Active uniquement la collecte des données d’allocation de mémoire.|  
       |**/tracegclife**|Active à la fois la collecte des données d’allocation de mémoire et des données de durée de vie des objets.|  

4. Démarrez le profileur. Type :  

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  

   - L’option [/start](../profiling/start.md)**:trace** initialise le profileur.  

   - L’option [/output](../profiling/output.md)**:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données de profilage (.*vsp*).  

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:trace**.  

   | Option | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire de processus est listé dans la colonne Nom d’utilisateur, sous l’onglet **Processus** du Gestionnaire des tâches Windows. |
   | [/crosssession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si l’application s’exécute dans une autre session. L’identificateur de session est répertorié dans la colonne **ID de session**, sous l’onglet **Processus** du Gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Pour démarrer le profileur après avoir suspendu la collecte de données, ajoutez l’option **/globaloff** sur la ligne de commande **/start**. Utilisez **/globalon** pour reprendre le profilage. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/automark](../profiling/automark.md) **:** `Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/counter](../profiling/counter.md) **:** `Config` | Collecte des informations à partir du compteur de performances du processeur spécifié dans la configuration. Les informations du compteur sont ajoutées aux données collectées à chaque événement de profilage. |
   | [events](../profiling/events-vsperfcmd.md) **:** `Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier (.*etl*) distinct. |


5. Démarrez l’application cible dans la fenêtre d’invite de commandes.  

## <a name="control-data-collection"></a>Contrôler la collecte des données  
 Pendant l’exécution de l’application cible, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier à l’aide des options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.  

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données  

-   Les paires d’options **VSPerfCmd** suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  

    |Option|Description|  
    |------------|-----------------|  
    |[/globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|  

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage  
 Pour mettre fin à une session de profilage, fermez l’application qui exécute le composant instrumenté, puis appelez l’option [/shutdown](../profiling/shutdown.md) de **VSPerfCmd** pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /off** efface les variables d’environnement de profilage.  

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage  

1.  Fermez l’application cible.  

2.  Fermez le profileur. Type :  

     **VSPerfCmd /shutdown**  

3.  (Facultatif) Effacez les variables d’environnement de profilage. Type :  

     **VSPerfCmd /off**  

## <a name="see-also"></a>Voir aussi  
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Vues des données de la mémoire .NET](../profiling/dotnet-memory-data-views.md)