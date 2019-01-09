---
title: Attacher le profileur à une application web ASP.NET pour collecter des données de mémoire
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 19eb50c967a208a6c5267688ee919f0faaca548e
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592961"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Procédure : Attacher le profileur à une application web ASP.NET pour collecter des statistiques d’application en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à une application web ASP.NET et collecter des statistiques de performances à l’aide de la méthode d’échantillonnage.  

> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
>  Pour ajouter des données d’interaction de couche à une exécution de profilage, vous devez utiliser des procédures spécifiques avec les outils de profilage en ligne de commande. Consultez [Collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
> 
>  Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.    

 Pour collecter les données de performances à partir d’une application web ASP.NET, les variables d’environnement appropriées doivent être initialisées, et l’ordinateur qui héberge l’application web ASP.NET doit être redémarré pour configurer le serveur web pour le profilage.  

 Vous attachez ensuite le profileur au processus de travail ASP.NET qui héberge votre site web. Quand le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte des données.  

 Pour mettre fin à une session de profilage, vous devez détacher le profileur de l’application profilée et l’arrêter explicitement. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.  

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>Démarrer le profileur et l’attacher à une application web ASP.NET  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Pour attacher le profileur à une application web ASP.NET  

1. Ouvrez une fenêtre d’invite de commandes.  

2. Initialisez les variables d’environnement de profilage. Type :  

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]  

   -   **/globalsampleon** permet l’échantillonnage.  

   -   **/samplelineoff** désactive l’assignation des données collectées à des lignes de code source spécifiques. Lorsque cette option est spécifiée, les données sont assignées uniquement aux fonctions.  

3. Redémarrez l'ordinateur.  

4. Démarrez le profileur. Tapez :**VSPerfCmd** [/start](../profiling/start.md)**:sample** [/output](../profiling/output.md)**:**`OutputFile`[`Options`]  

   - L’option **/start:sample** initialise le profileur.  

   - L’option **/output:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).  

     Vous pouvez utiliser une des options suivantes avec l’option **/start:sample**.  

   > [!NOTE]
   >  Les options **/user** et **/crosssession** sont généralement nécessaires pour les applications ASP.NET.  

   | Option | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus de travail ASP.NET. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire de processus est listé dans la colonne **Nom d’utilisateur**, sous l’onglet **Processus** du Gestionnaire des tâches Windows. |
   | [/crosssession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’identificateur de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/automark](../profiling/automark.md) **:** `Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl). |


5. Démarrez l’application web ASP.NET de façon classique.  

6. Attachez le profileur au processus de travail ASP.NET. Tapez :**VSPerfCmd** [/attach](../profiling/attach.md)**:**{`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

   -   `PID` spécifie l’ID de processus du processus de travail ASP.NET ; `ProcName` spécifie le nom du processus de travail. Vous pouvez afficher les ID et les noms de processus de tous les processus en cours d’exécution dans le Gestionnaire des tâches de Windows.  

   -   Par défaut, les données de performances sont échantillonnées tous les 10 000 000 cycles d’horloge ininterrompus du processeur. Ceci représente environ 100 fois par seconde sur un processeur à 1 GHz. Vous pouvez spécifier une des options de **VSPerfCmd** suivantes pour modifier l’intervalle de cycles d’horloge ou pour spécifier un autre événement d’échantillonnage.  

   |Événement d'échantillon|Description|  
   |------------------|-----------------|  
   |[/timer](../profiling/timer.md) **:** `Interval`|Remplace l’intervalle d’échantillonnage par le nombre de cycles d’horloge ininterrompus spécifiés par `Interval`.|  
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Remplace l’événement d’échantillonnage par les erreurs de page. Si `Interval` est spécifié, définit le nombre d’erreurs de page entre chaque échantillon. La valeur par défaut est 10.|  
   |[/sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Remplace l’événement d’échantillonnage par des appels système du processus vers le noyau du système d’exploitation (syscalls). Si `Interval` est spécifié, définit le nombre d’appels entre chaque échantillon. La valeur par défaut est 10.|  
   |[/counter](../profiling/counter.md) **:** `Config`|Remplace l’événement et l’intervalle d’échantillonnage par le compteur de performances du processeur et l’intervalle spécifié dans `Config`.|  
   |[/targetclr](../profiling/targetclr.md) **:** `Version`|Spécifie la version du common language runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.|  

   -   **/targetclr:** `Version` spécifie la version du CLR à profiler lorsque plusieurs versions du runtime sont chargées dans une application. Optionnel.  

## <a name="control-data-collection"></a>Contrôler la collecte des données  
 Pendant l’exécution de l’application, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier avec les options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.  

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données  

-   Les paires d’options **VSPerfCmd** suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  

    |Option|Description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par le `PID`.|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** commence à collecter des données pour le processus spécifié par le `PID` ou le nom de processus (ProcName). **/detach** arrête la collecte des données pour le processus spécifié ou pour tous les processus, si aucun processus n’est spécifié.|  

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage  
 Pour terminer une session de profilage, fermez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], puis utilisez la commande **IISReset** d’Internet Information Services (IIS) pour fermer le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Appelez l’option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage.  

 La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement du profilage. Vous devez redémarrer l’ordinateur pour que les nouveaux paramètres d’environnement soient appliqués.  

 La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement de profilage. Toutefois, la configuration du système n’est pas réinitialisée tant que l’ordinateur n’a pas été redémarré.  

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage  

1. Effectuez une des opérations suivantes pour détacher le profileur de l’application cible :  

   - Tapez **VSPerfCmd /detach**  

      ou  

   - Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  

2. Fermez le profileur. Tapez :**VSPerfCmd** [/shutdown](../profiling/shutdown.md)  

3. (Facultatif) Effacez les variables d’environnement de profilage. Type :  

    **VSPerfCmd /globaloff**  

4. Redémarrez l'ordinateur.  

## <a name="see-also"></a>Voir aussi  
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)