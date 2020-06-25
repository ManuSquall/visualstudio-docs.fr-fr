---
title: Ligne de commande du profileur-service .NET d’instrumentation, récupération des données de mémoire
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 042f01bcc53f12c240276374bdce5fb965c67be4
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330121"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Guide pratique pour instrumenter un service .NET Framework et collecter des données de mémoire en utilisant la ligne de commande du profileur
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour instrumenter un service .NET Framework et collecter des données d’utilisation de la mémoire. Vous pouvez collecter les données d’allocation de mémoire, ou bien collecter à la fois les données d’allocation de mémoire et les données de durée de vie des objets.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Vous ne pouvez pas profiler un service avec la méthode d’instrumentation si le service ne peut pas être redémarré après le démarrage de l’ordinateur, comme un service qui démarre au démarrage du système d’exploitation.
>
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

## <a name="start-the-profiling-session"></a>Démarrer la session de profilage
 Pour collecter des données de performances auprès d’un service .NET Framework, vous utilisez l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement appropriées et l’outil [VSInstr.exe](../profiling/vsinstr.md) pour créer une copie instrumentée du fichier binaire du service.

 L’ordinateur qui héberge le service doit être redémarré pour être configuré pour le profilage. Vous devez également démarrer le service manuellement à partir du Gestionnaire de contrôle des services. Vous démarrez ensuite le profileur, puis le service .NET Framework.

 Lorsque le composant instrumenté est exécuté, les données de mémoire sont automatiquement rassemblées dans un fichier de données. Vous pouvez suspendre et reprendre la collecte des données pendant la session de profilage.

 Pour mettre fin à une session de profilage, fermez le service et arrêtez explicitement le profileur. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.

#### <a name="to-begin-profiling-a-net-framework-service"></a>Pour démarrer le profilage d’un service .NET Framework

1. Ouvrir une fenêtre d’invite de commandes.

2. Utilisez l’outil **VSInstr** pour générer une version instrumentée du fichier binaire du service.

3. Utilisez le Gestionnaire de contrôle des services pour remplacer le fichier binaire d’origine par la version instrumentée. Vérifiez que le type de démarrage du service est défini sur Manuel.

4. Initialisez les variables d’environnement de profilage. Tapez :

    **VSPerfClrEnv** {**/globaltracegc** &#124; **/globaltracegclife**}

   - **/globaltracegc** et **/globaltracegclife** activent la collecte des données d’allocation de mémoire et de durée de vie des objets.

       |Option|Description|
       |------------|-----------------|
       |**/globaltracegc**|Collecte uniquement les données d’allocation de mémoire.|
       |**/globaltracegclife**|Collecte les données d’allocation de mémoire et les données de durée de vie des objets.|

5. Redémarrez l’ordinateur.

6. Ouvrir une fenêtre d’invite de commandes.

7. Démarrez le profileur. Tapez :

    **VSPerfCmd**  [/Start](../profiling/start.md) **: trace**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - L’option **/start: contention** initialise le profileur.

   - L’option **/Output :** `OutputFile` est requise avec **/Start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:sample**.

   > [!NOTE]
   > Les options **/user** et **/crosssession** sont généralement nécessaires pour les services.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus de travail ASP.NET. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que l’utilisateur connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’ID de session est indiqué dans la colonne **ID de session** sous l’onglet **processus** du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/WaitStart](../profiling/waitstart.md)[**:** `Interval` ] | Spécifie le nombre de secondes à attendre que le profileur s’initialise avant qu’il retourne une erreur. Si `Interval` n’est pas spécifié, le profileur attend indéfiniment. Par défaut, **/start** retourne immédiatement. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Pour démarrer le profileur après avoir suspendu la collecte de données, ajoutez l’option **/globaloff** sur la ligne de commande **/start**. Utilisez **/globalon** pour reprendre le profilage. |
   | [/Counter](../profiling/counter.md) **:**`Config` | Collecte des informations à partir du compteur de performances du processeur spécifié dans la configuration. Les informations de compteur sont ajoutées aux données collectées à chaque événement de profilage. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un (.* fichier ETL*). |

8. Si nécessaire, démarrez le service.

9. Attachez le profileur au service. Tapez :

     **VSPerfCmd /attach:** `PID`&#124;`ProcessName`

    - Spécifiez l’ID ou le nom de processus du service. Vous pouvez afficher les ID et les noms de processus de tous les processus en cours d’exécution dans le Gestionnaire des tâches de Windows.

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Pendant l’exécution du service, vous pouvez contrôler la collecte des données en démarrant et en arrêtant l’écriture des données dans le fichier avec les options de *VSPerfCmd.exe*. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options **VSPerfCmd** suivantes démarrent et arrêtent la collecte de données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour mettre fin à une session de profilage, fermez l’application qui exécute le composant instrumenté, puis démarrez l’option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage. La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement du profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Arrêtez le service à partir du Gestionnaire de contrôle des services.

2. Fermez le profileur. Tapez :

     **VSPerfCmd /shutdown**

3. Quand vous avez terminé le profilage, effacez les variables d’environnement de profilage. Tapez :

     **VSPerfClrEnv /globaloff**

     Remplacez le module instrumenté par l’original. Si nécessaire, reconfigurez le type de démarrage du service.

4. Redémarrez l’ordinateur.

## <a name="see-also"></a>Voir aussi
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
- [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)
