---
title: Guide pratique pour attacher le profileur à un service .NET et collecter des statistiques d’application en utilisant la ligne de commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc65d8afc75229caed524e5414abe4595d4de65a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840129"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Comment : attacher le profileur à un service .NET pour collecter des statistiques d'applications en utilisant la ligne de commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour attacher le profileur à un service .NET Framework et pour collecter des statistiques de performances avec la méthode d’échantillonnage.  

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
> Les outils en ligne de commande des outils de profilage se trouvent dans le sous-répertoire \Team Tools\Performance Tools du répertoire d’installation de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande. Pour plus d’informations, consultez [Spécification du chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> L’ajout de données d’interaction de couche à une exécution de profilage nécessite des procédures spécifiques avec les outils de profilage en ligne de commande. Consultez [collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 Pour collecter des données de performances auprès d’une application .NET Framework, vous devez utiliser l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement appropriées. Vous devez ensuite redémarrer l’ordinateur qui héberge le service et configurer cet ordinateur pour le profilage. Vous attachez ensuite le profileur au processus du service. Quand le profileur est attaché au service, vous pouvez suspendre et reprendre la collecte de données.  

 Pour mettre fin à une session de profilage, vous devez détacher le profileur du service et l’arrêter explicitement. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.  

## <a name="attaching-the-profiler"></a>Attachement du profileur  

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Pour attacher le profileur à un service .NET Framework  

1. Installez le service.  

2. Ouvrir une fenêtre d’invite de commandes.  

3. Initialisez les variables d’environnement de profilage. Tapez :  

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]  

   - **/globalsampleon** permet l’échantillonnage.  

   - **/samplelineoff** désactive l’assignation des données collectées à des lignes de code source spécifiques. Lorsque cette option est spécifiée, les données sont assignées uniquement aux fonctions.  

4. Redémarrez l’ordinateur.  

5. Ouvrir une fenêtre d’invite de commandes.  

6. Démarrez le profileur. Tapez :  

    **VSPerfCmd**  [/Start](../profiling/start.md) **: exemple**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]  

   - L’option **/Start : Sample** Initialise le profileur.  

   - L’option **/Output :** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).  

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:sample**.  

   > [!NOTE]
   > Les options **/user** et **/crosssession** sont généralement nécessaires pour les services.  

   |                                 Option                                  |                                                                                                                                          Description                                                                                                                                           |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` |      Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows.       |
   |              [/CrossSession](../profiling/crosssession.md)              | Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si le service s’exécute dans une autre session. L’ID de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   |    [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`     |                                                                                                           Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage.                                                                                                            |
   |         [/AutoMark](../profiling/automark.md) **:**`Interval`          |                                                                         À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms.                                                                          |
   |       [/Events](../profiling/events-vsperfcmd.md) **:**`Config`        |                                                                            Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl).                                                                            |

7. Si nécessaire, démarrez le service.  

8. Attachez le profileur au service. Tapez :  

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:** { `PID`&#124;`ProcName` } [ `Sample Event` ] [[/TargetCLR](../profiling/targetclr.md)**:** `Version` ]    

   - Spécifiez l’ID (`PID`) ou le nom de processus (ProcName) du service. Vous pouvez afficher les ID et les noms de processus de tous les processus en cours d’exécution dans le Gestionnaire des tâches de Windows.  

     Par défaut, les données de performances sont échantillonnées tous les 10 000 000 cycles d’horloge ininterrompus du processeur. Ceci représente environ 100 échantillons par seconde sur un processeur 1 GHz. Vous pouvez spécifier l’une des options suivantes pour modifier l’intervalle de cycle d’horloge ou pour spécifier un autre événement d’échantillonnage.  

   |Événement d’échantillonnage|Description|  
   |------------------|-----------------|  
   |[/Timer](../profiling/timer.md) **:**`Interval`|Remplace l’intervalle d’échantillonnage par le nombre de cycles d’horloge sans interruption spécifié par `Interval`.|  
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Remplace l’événement d’échantillonnage par les erreurs de page. Si `Interval` est spécifié, définit le nombre d’erreurs de page entre chaque échantillon. La valeur par défaut est 10.|  
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Remplace l’événement d’échantillonnage par des appels système du processus vers le noyau du système d’exploitation (syscalls). Si `Interval` est spécifié, définit le nombre d’appels entre chaque échantillon. La valeur par défaut est 10.|  
   |[/Counter](../profiling/counter.md) **:**`Config`|Remplace l’événement et l’intervalle d’échantillonnage par le compteur de performances du processeur et l’intervalle spécifiés dans `Config`.|  

   - **TargetCLR :** `Version` spécifie la version du common language runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application. facultatif.  

## <a name="controlling-data-collection"></a>Contrôle de la collection de données  
 Quand le service s’exécute, vous pouvez utiliser les options de **VSPerfCmd.exe** pour démarrer et arrêter l’écriture des données dans le fichier de données du profileur. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.  

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données  

- Les paires d’options **VSPerfCmd** suivantes démarrent et arrêtent la collecte de données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  

    |Option|Description|  
    |------------|-----------------|  
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|  
    |**/Attach :**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[ : { `PID`&#124;`ProcName` }]|**/attach** commence à collecter des données pour le processus spécifié par l’ID ou le nom de processus. **/Detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus spécifique n’est spécifié.|  

## <a name="ending-the-profiling-session"></a>Fin d’une session de profilage  
 Pour mettre fin à une session de profilage, vous devez détacher le profileur de tous les processus profilés et l’arrêter explicitement. Vous pouvez détacher le profileur d’une application profilée avec la méthode d’échantillonnage en fermant l’application ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage.  

 La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement de profilage. Toutefois, la configuration du système n’est pas réinitialisée tant que l’ordinateur n’a pas été redémarré.  

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage  

1. Effectuez une des opérations suivantes pour détacher le profileur de l’application cible :  

    - Arrête le service.  

         - ou -  

    - Tapez **VSPerfCmd/detach**  

2. Fermez le profileur. Tapez :  

     **VSPerfCmd /shutdown**  

3. (Facultatif) Effacez les variables d’environnement de profilage. Tapez :  

     **VSPerfClrEnv /globaloff**  

4. Redémarrez l’ordinateur.  

## <a name="see-also"></a>Voir aussi  
 [Profilage de services](../profiling/command-line-profiling-of-services.md)   
 [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)
