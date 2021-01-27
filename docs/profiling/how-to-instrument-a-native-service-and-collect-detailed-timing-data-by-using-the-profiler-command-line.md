---
title: Ligne de commande du profileur-instrumentation Native service, recevoir des données de minutage
description: Découvrez comment utiliser les outils en ligne de commande Outils de profilage Visual Studio pour collecter des données de temporisation détaillées pour un service C/C++ natif.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 2a4209db8856dd81ad6e74112b2907422826fe1c
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883564"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Guide pratique pour instrumenter un service natif et collecter des données temporelles détaillées en utilisant la ligne de commande du profileur
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour instrumenter un service natif (C/C++) et collecter des données chronologiques détaillées.

> [!NOTE]
> Vous ne pouvez pas profiler un service avec la méthode d’instrumentation si le service ne peut pas être redémarré après le démarrage de l’ordinateur, comme un service qui démarre seulement quand le système d’exploitation démarre.
>
> Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes, ou l’ajouter à la commande.

 Pour collecter des données chronologiques détaillées à partir d’un service natif avec la méthode d’instrumentation, vous utilisez l’outil [VSInstr.exe](../profiling/vsinstr.md) pour générer une version instrumentée du composant. Vous remplacez ensuite la version non instrumentée du service par la version instrumentée, en vérifiant que le service est configuré pour démarrer manuellement. Vous démarrez ensuite le profileur.

 Quand le service est démarré, les données chronologiques sont collectées automatiquement dans un fichier de données. Vous pouvez suspendre et reprendre la collecte des données pendant la session de profilage.

 Pour mettre fin à une session de profilage, vous désactivez le service, puis vous arrêtez explicitement le profileur.

## <a name="start-the-application-with-the-profiler"></a>Démarrer l’application avec le profileur

#### <a name="to-start-profiling-a-native-service"></a>Pour démarrer le profilage d’un service natif

1. Ouvrir une fenêtre d’invite de commandes.

2. Utilisez l’outil **VSInstr** pour générer une version instrumentée du fichier binaire du service.

3. Remplacez le fichier binaire d’origine par la version instrumentée. Dans le Gestionnaire de contrôle des services Windows, vérifiez que le type de démarrage du service est défini sur Manuel.

4. Démarrez le profileur. Tapez :

    **VSPerfCmd** [/Start](../profiling/start.md) **: trace**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - L’option **/Start : trace** Initialise le profileur.

   - L’option **/Output :** `OutputFile` est requise avec **/Start**. `OutputFile` Spécifie le nom et l’emplacement des données de profilage (.*vsp*).

     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:trace**.

   > [!NOTE]
   > Les options **/user** et **/crosssession** sont généralement nécessaires pour les applications ASP.NET.

   | Option | Description |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus de travail ASP.NET. Cette option est nécessaire si le processus s’exécute sous le compte d’un utilisateur autre que l’utilisateur connecté. Le propriétaire du processus est listé dans la colonne **nom d’utilisateur** sous l’onglet **processus** du gestionnaire des tâches de Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Active le profilage des processus dans d’autres sessions ouvertes. Cette option est nécessaire si l’application ASP.NET s’exécute dans une autre session. L’ID de session est répertorié dans la colonne ID de session, sous l’onglet Processus du Gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**. |
   | [/WaitStart](../profiling/waitstart.md)[**:** `Interval` ] | Spécifie le nombre de secondes à attendre que le profileur s’initialise avant qu’il retourne une erreur. Si `Interval` n’est pas spécifié, le profileur attend indéfiniment. Par défaut, **/start** retourne immédiatement. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Pour démarrer le profileur après avoir suspendu la collecte de données, ajoutez l’option **/globaloff** sur la ligne de commande **/start**. Utilisez **/globalon** pour reprendre le profilage. |
   | [/Counter](../profiling/counter.md) **:**`Config` | Collecte des informations à partir du compteur de performances du processeur spécifié dans la configuration. Les informations de compteur sont ajoutées aux données collectées à chaque événement de profilage. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un (.*fichier ETL*). |

5. Démarrez le service à partir du Gestionnaire de contrôle des services.

## <a name="control-data-collection"></a>Contrôler la collecte des données
 Quand le service s’exécute, vous pouvez utiliser les options de *VSPerfCmd.exe* pour démarrer et arrêter l’écriture des données dans le fichier de données du profileur. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, comme le démarrage ou l’arrêt du service.

#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données

- Les paires d’options **VSPerfCmd** suivantes démarrent et arrêtent la collecte de données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.

    |Option|Description|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Démarre (**/threadon**) ou arrête (**/threadoff**) la collecte des données pour le thread spécifié par l’ID de thread (`TID`).|

## <a name="end-the-profiling-session"></a>Arrêter la session de profilage
 Pour mettre fin à une session de profilage, arrêtez le service qui exécute le composant instrumenté, puis appelez l’option **VSPerfCmd**[/shutdown](../profiling/shutdown.md) pour désactiver le profileur et fermer le fichier de données de profilage.

#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage

1. Arrêtez le service à partir du Gestionnaire de contrôle des services.

2. Fermez le profileur. Tapez :

     **VSPerfCmd /shutdown**

3. Remplacez le module instrumenté par l’original. Si nécessaire, reconfigurez le type de démarrage du service.

## <a name="see-also"></a>Voir aussi
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
- [Vues de données de la méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)
