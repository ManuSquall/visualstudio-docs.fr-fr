---
title: Création de rapports de profilage de base à partir de la ligne de commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f13921dea810ab2185e626cc2889f339d9d174f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537181"
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>Création de rapports de profilage de base à partir de la ligne de commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit les commandes VSPerfReport de base qui génèrent des rapports de valeurs séparées par des virgules (.csv) à partir d’un fichier de données de profilage .vsp ou .vsps. Pour une description de toutes les options de rapport, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Commandes de rapport  
 Utilisez une des commandes suivantes pour créer un rapport pour un fichier de données de profilage spécifié.  
  
 **VSPerfReport** `VSPFile` **/Summary:All**  
 Génère tous les rapports disponibles pour le fichier .vsp ou .vsps.  
  
 **VSPerfReport** `VSPFile` **/Summary :** `ReportType` [,`ReportType`...]  
 Génère les types de rapports spécifiés.  
  
 **VSPerfReport** `VSPFile` **/CallTrace**  
 Génère un rapport qui répertorie chaque événement de collecte de données. Instrumentation uniquement.  
  
## <a name="summary-report-type-parameters"></a>Paramètres des types de rapports récapitulatifs  
 Le tableau suivant décrit les rapports qui sont générés par l’option du type de rapport spécifié. Les colonnes d’un rapport dépendent de la méthode de profilage utilisée pour collecter les données.  
  
|Paramètre récapitulatif|Description du rapport|Informations de référence pour le rapport|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|Représente les relations parents/enfants entre les fonctions.|-   [Données d’échantillonnage](../profiling/caller-callee-view-sampling-data.md)<br />-   [Données d’instrumentation](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Données d’instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/caller-callee-view-contention-data.md)|  
|**Fonction**|Répertorie les données de profilage par fonction.|-   [Données d’échantillonnage](../profiling/functions-view-sampling-data.md)<br />-   [Données d’instrumentation](../profiling/functions-view-instrumentation-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Données d’instrumentation de la mémoire .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Représente les chemins d’exécution et les données de profilage des fonctions dans l’exécution du profilage.|-   [Données d’instrumentation](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Données d’échantillonnage](../profiling/call-tree-view-sampling-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Données d’instrumentation de la mémoire .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/call-tree-view-contention-data.md)|  
|**Compteur**|Répertorie les marques de profilage et les valeurs de compteur de performances Windows qui ont été collectés pendant l’exécution du profilage.|-   [Affichage des marques](../profiling/marks-view.md)|  
|**AdressesIP**|Répertorie les données de profilage par instruction.|-   [Données d’échantillonnage](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Données de conflit](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Répertorie la durée de vie des objets alloués.|-   [Vue durée de vie des objets](../profiling/object-lifetime-view.md)|  
|**Ligne**|Répertorie les données de profilage par ligne de code source.|-   [Données d’échantillonnage](../profiling/lines-view-sampling-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Données de conflit](../profiling/lines-view-contention-data.md)|  
|**En-tête**|Informations d’en-tête du fichier de données de profilage.|Spécifique au fichier.|  
|**Marque**|Marques de profilage collectées lors de l’exécution du profilage.|-   [Affichage des marques](../profiling/marks-view.md)|  
|**Module**|Répertorie les données de profilage par module.|-   [Données d’échantillonnage](../profiling/modules-view-sampling-data.md)<br />-   [Données d’instrumentation](../profiling/modules-view-instrumentation-data.md)<br />-   [Données d’échantillonnage de la mémoire .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Données d’instrumentation de la mémoire .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/modules-view-contention-data.md)|  
|**Processus**|Répertorie les données de profilage pour les processus.|-   [Vue processus](../profiling/process-view.md)<br />-   [Données de conflit](../profiling/process-view-contention-data.md)|  
|**Thread**|Répertorie les données de profilage pour les threads.|-   [Vue processus](../profiling/process-view.md)|  
|**Type**|Répertorie les données de profilage d’allocation par type.|-   [Allocation, vue](../profiling/dotnet-memory-allocations-view.md)|  
|**Contention**|Conflit de ressources.|-   [Conflits de ressources](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Répertorie les problèmes de règle de performance.|-   Répertorie le CheckId, la description et l’emplacement du code source du problème de la règle.|  
|**ETW**|Répertorie les événements de suivi d’événements pour Windows (ETW) collectés lors de l’exécution du profilage.|-   [Rapport ETW](../profiling/event-tracing-for-windows-etw-report.md)|
