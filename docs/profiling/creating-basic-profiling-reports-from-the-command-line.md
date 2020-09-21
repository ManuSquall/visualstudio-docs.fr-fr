---
title: Ligne de commande de profilage-créer des rapports de base
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c9ee74732c917ee4267e08f7ff1c60715971ed71
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808849"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Créer des rapports de profilage de base à partir de la ligne de commande
Cette rubrique décrit les commandes VSPerfReport de base qui génèrent des rapports de valeurs séparées par des virgules (.*csv*) à partir d’un fichier de données de profilage .*vsp* ou .*vsps*. Pour une description de toutes les options de rapport, consultez [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Commandes de rapport
 Utilisez une des commandes suivantes pour créer un rapport pour un fichier de données de profilage spécifié.

 **VSPerfReport** `VSPFile` **/Summary:All** Génère tous les rapports disponibles pour le fichier .*vsp* ou .*vsps*.

 **VSPerfReport** `VSPFile` **/Summary :** `ReportType` [,`ReportType`...] Génère les types de rapports spécifiés.

 **VSPerfReport** `VSPFile` **/CallTrace** Génère un rapport qui liste chaque événement de collecte de données. Instrumentation uniquement.

## <a name="summary-report-type-parameters"></a>Paramètres des types de rapport récapitulatifs
 Le tableau suivant décrit les rapports qui sont générés par l’option du type de rapport spécifié. Les colonnes d’un rapport dépendent de la méthode de profilage utilisée pour collecter les données.

|Paramètre récapitulatif|Description du rapport|Informations de référence pour le rapport|
|-----------------------|------------------------|----------------------|
|**CallerCallee**|Représente les relations parents/enfants entre les fonctions.|-   [Échantillonnage des données](../profiling/caller-callee-view-sampling-data.md)<br />-   [Données d’instrumentation](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Données d’instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/caller-callee-view-contention-data.md)|
|**Fonction**|Répertorie les données de profilage par fonction.|-   [Échantillonnage des données](../profiling/functions-view-sampling-data.md)<br />-   [Données d’instrumentation](../profiling/functions-view-instrumentation-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Données d’instrumentation de la mémoire .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/functions-view-contention-data.md)|
|**CallTree**|Représente les chemins d’exécution et les données de profilage des fonctions dans l’exécution du profilage.|-   [Données d’instrumentation](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Échantillonnage des données](../profiling/call-tree-view-sampling-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Données d’instrumentation de la mémoire .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/call-tree-view-contention-data.md)|
|**Compteur**|Répertorie les marques de profilage et les valeurs de compteur de performances Windows qui ont été collectés pendant l’exécution du profilage.|-   [Affichage des marques](../profiling/marks-view.md)|
|**AdressesIP**|Répertorie les données de profilage par instruction.|-   [Échantillonnage des données](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Données de conflit](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Life**|Répertorie la durée de vie des objets alloués.|-   [Vue durée de vie des objets](../profiling/object-lifetime-view.md)|
|**Ligne**|Répertorie les données de profilage par ligne de code source.|-   [Échantillonnage des données](../profiling/lines-view-sampling-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Données de conflit](../profiling/lines-view-contention-data.md)|
|**En-tête**|Informations d’en-tête du fichier de données de profilage.|Spécifique au fichier.|
|**Marque**|Marques de profilage collectées lors de l’exécution du profilage.|-   [Affichage des marques](../profiling/marks-view.md)|
|**Module**|Répertorie les données de profilage par module.|-   [Échantillonnage des données](../profiling/modules-view-sampling-data.md)<br />-   [Données d’instrumentation](../profiling/modules-view-instrumentation-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Données d’instrumentation de la mémoire .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/modules-view-contention-data.md)|
|**Processus**|Répertorie les données de profilage pour les processus.|-   [Vue processus](../profiling/process-view.md)<br />-   [Données de conflit](../profiling/process-view-contention-data.md)|
|**Thread**|Répertorie les données de profilage pour les threads.|-   [Vue processus](../profiling/process-view.md)|
|**Type**|Répertorie les données de profilage d’allocation par type.|-   [Allocation, vue](../profiling/dotnet-memory-allocations-view.md)|
|**Contention**|Conflit de ressources.|-   [Contentions de ressources](../profiling/resource-contentions-view-contention-data.md)|
|**RuleWarnings**|Répertorie les problèmes de règle de performance.|-   Répertorie le CheckId, la description et l’emplacement du code source du problème de la règle.|
|**ETW**|Répertorie les événements de suivi d’événements pour Windows (ETW) collectés lors de l’exécution du profilage.|-   [Rapport ETW](../profiling/event-tracing-for-windows-etw-report.md)|
