---
title: Attacher le profileur à une application ASP.NET pour collecter des données de mémoire
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: edf9fec93b8fed4e89e5e7cf0525d4f11ed326fa
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329348"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Guide pratique pour attacher le profileur à une application web ASP.NET et collecter des données de mémoire en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et collecter des données sur le nombre et la taille des allocations de mémoire du .NET Framework. Vous pouvez également collecter des données sur la durée de vie des objets en mémoire du .NET Framework.

> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

 Pour collecter des données de performances auprès d’une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vous devez utiliser l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement appropriées sur l’ordinateur qui héberge l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Vous devez ensuite redémarrer l’ordinateur pour configurer le serveur web pour le profilage.

 Vous utilisez ensuite l’outil [VSPerfCmd.exe](../profiling/vsperfcmd.md) pour attacher le profileur au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui héberge votre site web. Quand le profileur est attaché à l’application, vous pouvez suspendre et reprendre la collecte des données.

 Pour terminer une session de profilage, le profileur ne doit plus être attaché à l’application et doit être arrêté explicitement. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.

## <a name="attach-the-profiler"></a>Attacher le profileur

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Pour attacher le profileur à une application web ASP.NET

1. Ouvrez une fenêtre d’invite de commandes.

2. Initialisez les variables d’environnement de profilage. Tapez :

    **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]

   - Les options **/globalsamplegc** et **/globalsamplegclife** spécifient le type de données de mémoire à collecter.

        Spécifiez seulement une des options suivantes.

       |Option|Description|
       |------------|-----------------|
       |**/globalsamplegc**|Active la collecte des données d’allocation de mémoire.|
       |**/globalsamplegclife**|Active à la fois la collecte des données d’allocation de mémoire et celle des données de durée de vie des objets.|

   - L’option **/samplelineoff** désactive l’affectation des données collectées à des lignes de code source spécifiques. Quand cette option est spécifiée, les données sont affectées seulement au niveau des fonctions.

3. Redémarrez l’ordinateur pour définir la nouvelle configuration de l’environnement.

4. Ouvrez une fenêtre d’invite de commandes. Si nécessaire, définissez la variable d’environnement de chemin du profileur.

5. Démarrez le profileur. Tapez :

    **VSPerfCmd**  [/Start](../profiling/start.md) **: exemple**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - L’option **/Start : Sample** Initialise le profileur.

   - L’option **/Output :** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:sample**.

   > [!NOTE]
   > Les options **/user** et **/crosssession** sont généralement nécessaires pour les applications ASP.NET.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus de travail ASP.NET. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’identificateur de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/WaitStart](../profiling/waitstart.md) [**:** `Interval` ] | Spécifie le nombre de secondes à attendre que le profileur s’initialise avant qu’il retourne une erreur. Si `Interval` n’est pas spécifié, le profileur attend indéfiniment. Par défaut, **/start** retourne immédiatement. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl). |

6. Démarrez l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de manière habituelle.

7. Attachez le profileur au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Tapez :

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/TargetCLR](../profiling/targetclr.md)**:** `Version` ]  

   - L’ID de processus `(PID)` Spécifie l’ID de processus ou le nom du processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Vous pouvez afficher les ID de processus de tous les processus en cours d’exécution dans le gestionnaire des tâches de Windows.

   - **/TargetCLR :** `Version` spécifie la version du common language runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application.

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution de l’application, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier de données du profileur avec les options de **VSPerfCmd.exe**. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options **VSPerfCmd** suivantes démarrent et arrêtent la collecte de données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par le `PID`.|
    |**/Attach :**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124; : `ProcName` }]|**/attach** commence à collecter des données pour le processus spécifié par l’ID ou le nom de processus. **/Detach** arrête la collecte de données pour le processus spécifié ou pour tous les processus si aucun processus spécifique n’est spécifié.|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour mettre fin à une session de profilage, le profileur doit être détaché de l’application web. Vous pouvez arrêter la collecte des données d’une application profilée avec la méthode d’échantillonnage en redémarrant le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ou en appelant l’option **VSPerfCmd /detach**. Vous appelez ensuite l’option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement de profilage. Toutefois, la configuration du système n’est pas réinitialisée tant que l’ordinateur n’a pas été redémarré.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Effectuez l’une des opérations suivantes pour détacher le profileur de l’application cible :

   - Tapez **VSPerfCmd** [/detach](../profiling/detach.md)

      -ou-

   - Fermez le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Tapez :

     **IISReset /stop**

2. Fermez le profileur. Tapez :

    **VSPerfCmd /shutdown**

3. (Facultatif) Effacez les variables d’environnement de profilage. Tapez :

    **VSPerfCmd /globaloff**

4. Redémarrez l’ordinateur. Si nécessaire, redémarrez Internet Information Services (IIS). Tapez :

    **IISReset /start**

## <a name="see-also"></a>Voir aussi
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)
