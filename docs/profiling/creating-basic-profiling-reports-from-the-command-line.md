---
title: "Cr&#233;ation de rapports de profilage de base &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Cr&#233;ation de rapports de profilage de base &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit les commandes VSPerfReport de base qui génèrent des rapports au format .csv \(valeurs séparées par des virgules\) à partir d'un fichier de données de profilage .vsp ou .vsps.  Pour une description de toutes les options de rapport, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
## Commandes de rapport  
 Utilisez l'une des commandes suivantes pour créer un rapport pour un fichier de données de profilage spécifié.  
  
 **VSPerfReport** `VSPFile` **\/Summary:All**  
 Crée tous les rapports disponibles pour le fichier .vsp ou .vsps.  
  
 **VSPerfReport** `VSPFile` **\/Summary:**`ReportType`\[,`ReportType`...\]  
 Génère les types de rapport spécifiés.  
  
 **VSPerfReport** `VSPFile` **\/CallTrace**  
 Crée un rapport qui répertorie chaque événement de collecte de données.  Instrumentation seulement.  
  
## Résumés des paramètres de type de rapport  
 Le tableau suivant décrit les rapports créés par l'option de type de rapport spécifiée.  Les colonnes d'un rapport dépendent de la méthode de profilage utilisée pour collecter les données.  
  
|Résumé du paramètre|Description du rapport|Référence du rapport|  
|-------------------------|----------------------------|--------------------------|  
|**CallerCallee**|Représente les relations parent\/enfant entre les fonctions.|-   [Données d'échantillonnage](../profiling/caller-callee-view-sampling-data.md)<br />-   [Données d'instrumentation](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Données d'échantillonnage de la mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Données d'instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Répertorie les données de profilage par fonction.|-   [Données d'échantillonnage](../profiling/functions-view-sampling-data.md)<br />-   [Données d'instrumentation](../profiling/functions-view-instrumentation-data.md)<br />-   [Données d'échantillonnage de la mémoire .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Données d'instrumentation de la mémoire .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Représente les chemins d'exécution et les données de profilage des fonctions dans l'exécution du profilage.|-   [Données d'instrumentation](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Données d'échantillonnage](../profiling/call-tree-view-sampling-data.md)<br />-   [Données d'échantillonnage de la mémoire .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Données d'instrumentation de la mémoire .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/call-tree-view-contention-data.md)|  
|**Counter**|Répertorie les marques de profilage et les valeurs du compteur de performance Windows collectées pendant l'exécution du profilage.|-   [Marques, vue](../profiling/marks-view.md)|  
|**Ip**|Répertorie les données de profilage par instruction.|-   [Données d'échantillonnage](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Données d'échantillonnage de la mémoire .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Données de conflit](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Répertorie la durée de vie des objets alloués.|-   [Mode Durée de vie de l'objet](../profiling/object-lifetime-view.md)|  
|**Line**|Répertorie les données de profilage par ligne de code source.|-   [Données d'échantillonnage](../profiling/lines-view-sampling-data.md)<br />-   [Données d'échantillonnage de la mémoire .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Données de conflit](../profiling/lines-view-contention-data.md)|  
|**Header**|Informations d'en\-tête de fichier de données de profilage.|Spécifique au fichier.|  
|**Mark**|Marques de profilage collectées au cours de l'exécution du profilage.|-   [Marques, vue](../profiling/marks-view.md)|  
|**Module**|Répertorie les données de profilage pour les modules.|-   [Données d'échantillonnage](../profiling/modules-view-sampling-data.md)<br />-   [Données d'instrumentation](../profiling/modules-view-instrumentation-data.md)<br />-   [Données d'échantillonnage de la mémoire .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Données d'instrumentation de la mémoire .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Données de conflit](../profiling/modules-view-contention-data.md)|  
|**Process**|Répertorie les données de profilage pour les processus.|-   [Mode Processus](../profiling/process-view.md)<br />-   [Données de conflit](../profiling/process-view-contention-data.md)|  
|**Thread**|Répertorie les données de profilage pour les threads.|-   [Mode Processus](../profiling/process-view.md)|  
|**Type**|Répertorie les données de profilage d'allocation par type.|-   [Mode Allocations](../profiling/dotnet-memory-allocations-view.md)|  
|**Contention**|Conflits de ressources.|-   [Conflits de ressources](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Répertorie les problèmes de règles de performance.|-   Répertorie le CheckId, la description et l'emplacement de code source du problème de la règle.|  
|**ETW**|Répertorie tous les événements ETW \(Event Tracing for Windows\) collectés au cours de l'exécution du profilage.|-   [Rapport ETW](../profiling/event-tracing-for-windows-etw-report.md)|