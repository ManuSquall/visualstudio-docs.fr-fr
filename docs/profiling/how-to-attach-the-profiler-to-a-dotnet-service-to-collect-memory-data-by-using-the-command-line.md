---
title: Attacher le profileur au service .NET pour collecter des données de mémoire
description: Utilisez les outils en ligne de commande Visual Studio Outils de profilage pour attacher le profileur à un service .NET Framework et collecter des données de mémoire.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: e31404c07fb7093bb2bd1114340cdb87d3c8558a
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800586"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-service-to-collect-memory-data-by-using-the-command-line"></a>Comment : attacher le profileur à un service de .NET Framework pour collecter des données de mémoire à l’aide de la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à un service .NET Framework et collecter des données de mémoire. Vous pouvez collecter des données sur le nombre et la taille des allocations de mémoire, ainsi que des données sur la durée de vie des objets en mémoire.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

 Pour collecter des données de mémoire auprès d’un service .NET Framework, vous utilisez l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement appropriées sur l’ordinateur qui héberge le service. L’ordinateur doit être redémarré pour être configuré pour le profilage.

 Vous utilisez ensuite l’outil [VSPerfCmd](../profiling/vsperfcmd.md) pour attacher le profileur au processus du service. Lorsque le profileur est attaché au service, vous pouvez suspendre et reprendre la collecte de données.

 Pour mettre fin à une session de profilage, vous devez détacher le profileur du service et l’arrêter explicitement. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.

## <a name="attach-the-profiler"></a>Attacher le profileur

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Pour attacher le profileur à un service .NET Framework

1. Si nécessaire, installez le service.

2. Ouvrir une fenêtre d’invite de commandes.

3. Initialisez les variables d’environnement de profilage. Tapez :

    **VSPerfClrEnv** {**/globalsamplegc /globalsamplegclife**}[**/samplelineoff**]

   - Les options **/globalsamplegc** et **/globalsamplegclife** spécifient le type de données de mémoire à collecter. Spécifiez seulement une des options suivantes.

     **/globalsamplegc** permet d’activer la collecte de données d’allocation de mémoire.

     **/globalsamplegclife** permet d’activer la collecte de données d’allocation de mémoire et de données de durée de vie des objets.

   - L’option **/samplelineoff** désactive la collecte des données de ligne de code source.

4. Redémarrez l’ordinateur pour définir la nouvelle configuration de l’environnement.

5. Si nécessaire, démarrez le service.

6. Ouvrir une fenêtre d’invite de commandes. Si nécessaire, ajoutez le chemin du profileur à la variable d’environnement PATH.

7. Démarrez le profileur. Tapez :

    **VSPerfCmd**  [/Start](../profiling/start.md) **: exemple**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - L’option **/Start : Sample** Initialise le profileur.

   - L’option **/Output :** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser une ou plusieurs des options suivantes avec l’option **/start:sample**.

   > [!NOTE]
   > Les options **/user** et **/crosssession** sont généralement nécessaires pour les services.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que l’utilisateur connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’ID de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur facultatifs du compte de connexion sous lequel le service s’exécute. Le compte de connexion figure dans la colonne « Ouvrir une session en tant que » du service dans le Gestionnaire de contrôle des services Windows. |
   | [/crosssession&#124;cs](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl). |

8. Attachez le profileur au service. Tapez :

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/TargetCLR](../profiling/targetclr.md)**:** `Version` ]  

   - Spécifiez l’ID de processus ou le nom de processus du service. Vous pouvez afficher les ID et les noms de processus de tous les processus en cours d’exécution dans le Gestionnaire des tâches de Windows.

   - **TargetCLR :** `Version` spécifie la version du common language runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application. facultatif.

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution du service, vous pouvez utiliser les options de *VSPerfCmd.exe* pour démarrer et arrêter l’écriture des données dans le fichier de données du profileur. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, comme le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options **VSPerfCmd** suivantes démarrent et arrêtent la collecte de données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |**/Attach :**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[ : { `PID`&#124;`ProcName` }]|**/attach** commence à collecter des données pour le processus spécifié par l’ID ou le nom de processus. **/detach** arrête la collecte des données pour le processus spécifié, ou pour tous les processus si aucun processus n’est spécifié.|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit pas être en train de collecter des données. Vous pouvez arrêter la collecte des données d’une application profilée avec la méthode d’échantillonnage en arrêtant le service ou appelant l’option **VSPerfCmd /detach**. Vous appelez ensuite l’option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement de profilage. Toutefois, la configuration du système n’est pas réinitialisée tant que l’ordinateur n’a pas été redémarré.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Effectuez une des opérations suivantes pour détacher le profileur de l’application cible :

    - Arrête le service.

         -ou-

    - Tapez **VSPerfCmd/detach**

2. Fermez le profileur. Tapez :

     **VSPerfCmd /shutdown**

3. (Facultatif) Effacez les variables d’environnement de profilage. Tapez :

     **VSPerfClrEnv /globaloff**

4. Redémarrez l'ordinateur.

## <a name="see-also"></a>Voir aussi
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
- [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)
