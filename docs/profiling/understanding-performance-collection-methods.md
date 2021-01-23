---
title: Fonctionnement des méthodes de collecte des performances | Microsoft Docs
description: En savoir plus sur les différents scénarios dans lesquels la collecte de données avec une méthode particulière peut être appropriée.
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3bbbef2c6f7bb2ab02731bfbac0dc60d75a3437
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722332"
---
# <a name="understand-performance-collection-methods"></a>Présenter les méthodes de collecte des performances

Les outils de profilage Visual Studio fournissent cinq méthodes de collecte des données de performances. Cet article décrit les différentes méthodes et suggère des scénarios dans lesquels la collecte de données avec une méthode particulière peut être appropriée.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et de Windows Server 2012 nécessitaient des changements significatifs dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’exécution des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Méthode|Description|
|------------|-----------------|
|[Échantillonnage](#sampling)|Collecte des données statistiques sur le travail effectué par une application.|
|[Instrumentation](#instrumentation)|Collecte des informations de minutage détaillées sur chaque appel de fonction.|
|[Concurrency](#concurrency)|Recueille des informations détaillées sur les applications multithread.|
|[Mémoire .NET](#net-memory)|Collecte des informations détaillées sur l’allocation et la garbage collection de la mémoire .NET.|
|[Interaction de couche](#tier-interaction)|Collecte des informations sur les appels de fonction ADO.NET synchrones à une base de données SQL Server.<br /><br /> Toutes les éditions de Visual Studio peuvent collecter des données de profil d’interaction de couche. Toutefois, vous pouvez afficher ces données uniquement dans Visual Studio Enterprise.|

À l’aide de certaines méthodes de profilage, vous pouvez également collecter des données supplémentaires, telles que des compteurs de performances logicielles et matérielles. Pour plus d’informations, consultez [Collecte des données de performances supplémentaires](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>échantillonnage

La méthode de profilage par échantillonnage collecte des données statistiques sur le travail effectué par une application pendant une exécution du profilage. La méthode d’échantillonnage est légère et n’a que peu d’effet sur l’exécution des méthodes de l’application.

L’échantillonnage est la méthode par défaut des outils de profilage Visual Studio. Elle est utile pour les tâches suivantes :

- Explorations initiales des performances de votre application
- Examen des problèmes de performances qui impliquent l’utilisation du microprocesseur (UC)

La méthode de profilage par échantillonnage interrompt le processeur de l’ordinateur à des intervalles définis et collecte la pile des appels de fonction. Les nombres d’échantillons exclusifs sont incrémentés pour la fonction en cours d’exécution. Les nombres inclusifs sont incrémentés pour toutes les fonctions appelées sur la pile des appels. Les rapports d’échantillonnage présentent les totaux de ces nombres pour les modules, les fonctions, les lignes de code source et les instructions profilés.

Par défaut, le profileur définit l’intervalle d’échantillonnage sur la base des cycles de l’UC. Vous pouvez remplacer le type d’intervalle par un autre compteur de performances de l’UC ou définir le nombre d’événements de compteur pour l’intervalle. Vous pouvez également collecter des données de profilage d’interaction de couche (TIP). Ces données fournissent des informations sur les requêtes effectuées dans une base de données SQL Server par le biais de ADO.NET.

[Collecter les statistiques de performances à l’aide de l’échantillonnage](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Comprendre le fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)

[Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>Instrumentation

La méthode de profilage par instrumentation collecte un minutage détaillé pour les appels de fonction dans une application profilée. Le profilage par instrumentation est utile pour les tâches suivantes :

- Examen des goulots d’étranglement d’entrée/sortie tels que les e/s disque
- Fermer l’examen d’un module ou d’un ensemble de fonctions particulier

La méthode d’instrumentation injecte du code dans un fichier binaire. Le code capture les informations de minutage pour toutes les fonctions dans le fichier instrumenté et chaque appel de fonction effectué par ces fonctions. L’instrumentation identifie également quand une fonction appelle le système d’exploitation pour des opérations telles que l’écriture dans un fichier.

Les rapports d’instrumentation utilisent ces quatre valeurs pour représenter le temps total passé dans une fonction ou une ligne de code source :

- Temps inclusif écoulé : temps total passé à exécuter la fonction ou la ligne de code source.

- Temps inclusif d’application-temps consacré à l’exécution de la fonction ou de la ligne de code source. Les appels au système d’exploitation sont exclus.

- Temps exclusif écoulé : temps passé à exécuter la fonction ou la ligne de code source. Les appels à d’autres fonctions sont exclus.

- Application exclusive-temps passé à exécuter la fonction ou la ligne de code source. Les appels au système d’exploitation ou à d’autres fonctions sont exclus.

Vous pouvez également collecter les compteurs de performance du processeur et des logiciels à l’aide de la méthode d’instrumentation.

[Comprendre le fonctionnement des valeurs de données d’instrumentation](../profiling/understanding-instrumentation-data-values.md)

[Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Vues de données de la méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>Accès concurrentiel

Le profilage d’accès concurrentiel collecte des informations sur les applications multithread. Le profilage de conflit de ressources collecte les informations détaillées de la pile d’appels chaque fois que les threads concurrents attendent l’accès à une ressource partagée. La visualisation concurrentielle collecte également des informations plus générales sur la façon dont votre application multithread interagit avec :

- Automatiquement.
- Le matériel.
- Système d'exploitation.
- Autres processus sur l’ordinateur hôte.

Les rapports de conflit de ressources affichent le nombre total de conflits. Ils indiquent également la durée totale pendant laquelle les modules, les fonctions, les lignes de code source et les instructions ont attendu une ressource. Les graphiques chronologiques affichent les conflits tels qu’ils se sont produits.

Le visualiseur concurrentiel affiche des informations graphiques pour vous aider à localiser :

- Goulots d’étranglement des performances.
- Sous-exploitation de l’UC.
- Conflit de threads.
- Migration de threads.
- Délais de synchronisation.
- Zones d’e/s avec chevauchement.

  Dans la mesure du possible, la sortie graphique est liée aux données de la pile des appels et du code source. Les données de visualisation concurrentielle peuvent être collectées uniquement pour les applications de ligne de commande et les applications Windows.

[Comprendre les valeurs de données de conflit de ressources](../profiling/understanding-resource-contention-data-values.md)

[Collecter les données concurrentielles de threads et de processus](../profiling/collecting-thread-and-process-concurrency-data.md)

[Vues de données de conflit de ressources](../profiling/resource-contention-data-views.md)

[Visualiseur concurrentiel](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>Mémoire .NET

La méthode de profilage pour l’allocation de mémoire .NET interrompt le processeur à chaque allocation d’un objet .NET Framework dans une application profilée. Lorsque le profileur collecte également les données de durée de vie des objets, il interrompt le processeur après chaque .NET Framework garbage collection.

Le profileur collecte des informations sur le type, la taille et le nombre d’objets créés dans une allocation ou détruits dans garbage collection.

- Quand un événement d’allocation se produit, le profileur collecte des informations supplémentaires sur la pile d’appel des fonctions. Le profileur incrémente le nombre d’allocations exclusifs pour la fonction en cours d’exécution. Elle incrémente également les nombres inclusifs de toutes les fonctions appelées sur la pile des appels. Les rapports .NET présentent les totaux de ces nombres pour les types profilés, les modules, les fonctions, les lignes de code source et les instructions.

- Quand garbage collection se produit, le profileur collecte des données sur les objets détruits et sur les objets dans chaque génération de garbage collection. À la fin de l’exécution du profilage, le profileur enregistre les données relatives aux objets qui n’ont pas été explicitement détruits. Le rapport durée de vie des objets affiche les totaux de chaque type alloué dans l’exécution du profilage.

Vous pouvez utiliser le profilage de la mémoire .NET en mode d’échantillonnage ou en mode instrumentation. Le mode que vous sélectionnez n’affecte pas les rapports d’allocation et de durée de vie des objets qui sont propres au profilage de la mémoire .NET.

- Quand vous exécutez le profilage de la mémoire .NET en mode d’échantillonnage, le profileur utilise les événements d’allocation de mémoire comme intervalle. Il affiche également le nombre total d’objets et d’octets alloués en tant que valeurs inclusives et exclusives dans les rapports.

- Lorsque vous exécutez le profilage de la mémoire .NET en mode instrumentation, le profileur collecte des informations de temporisation détaillées avec les valeurs d’allocation inclusive et exclusive.

[Comprendre l’allocation de mémoire et les valeurs de données de durée de vie des objets](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[Collecter les données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Interaction de couche

Le profilage d’interaction de couche ajoute des informations à un fichier de données de profilage à propos des appels synchrones [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] entre une [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] page ou une autre application et une [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] base de données. Les données incluent le nombre et l’heure des appels, ainsi que les durées maximales et minimales. Vous pouvez ajouter des données d’interaction de couche aux données de profilage collectées avec les méthodes d’échantillonnage, d’instrumentation, de mémoire .NET ou de concurrence.

![Flux de données de profilage d’interaction de couche](../profiling/media/tierinteraction_profilingtools.png "Flux de données de profilage d’interaction de couche")

Pour plus d’informations sur les données d’interaction de couche collectées par les outils de profilage, consultez les articles suivants.

[Collecter les données d’interaction de couche](../profiling/collecting-tier-interaction-data.md)

[Vues d’interaction de couche](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Voir aussi

[Guide pratique pour collecter les données de performances d’un site web](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md)
