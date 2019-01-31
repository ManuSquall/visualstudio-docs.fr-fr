---
title: Vues de données de mémoire .NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method views
- profiling tools,.NET memory profiling views
ms.assetid: 79184d8e-769b-4ace-be2b-521147772081
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e67ee624b965156812c8ba9d1676a25308f617a7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941273"
---
# <a name="net-memory-data-views"></a>Vues des données de la mémoire .NET
Cette section contient des informations de référence sur les vues et les rapports des fichiers de données du profileur qui comprennent des données de profilage de mémoire .NET.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mode Résumé](../profiling/summary-view-dotnet-memory-data.md)  
 Répertorie les fonctions et les types qui ont alloué le plus de mémoire.  
  
 [Allocations, vue](../profiling/dotnet-memory-allocations-view.md)  
 Répertorie les types alloués lors de l’exécution du profilage, ainsi que les arborescences des appels (chemins d’exécution) qui ont provoqué l’allocation du type.  
  
 [Vue Durée de vie de l’objet](../profiling/object-lifetime-view.md)  
 Répertorie les types alloués lors de l’exécution du profilage, ainsi que le nombre d’instances, la taille en octets et la génération de garbage collection du type.  
  
 [Vue Arborescence des appels - Échantillonnage](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
 Affiche une arborescence hiérarchique qui représente les chemins d’exécution et les données d’allocation de mémoire des fonctions dans l’exécution du profilage.  
  
 [Vue Modules - Échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)  
 Organise les données d’allocation de mémoire .NET par module, et répertorie les fonctions, les lignes de code source et les instructions qui étaient en cours d’exécution lorsque la mémoire a été allouée.  
  
 [Vue Appelant/Appelé - Données d’échantillonnage de mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)  
 Répertorie les données d’allocation de mémoire d’une fonction sélectionnée, ainsi que les fonctions qui ont appelé la fonction sélectionnée et les fonctions qui ont été appelées par la fonction sélectionnée.  
  
 [Vue Fonctions - Échantillonnage](../profiling/functions-view-dotnet-memory-sampling-data.md)  
 Répertorie les données d’allocation de mémoire des fonctions lors de l’exécution du profilage.  
  
 [Vue Lignes - Échantillonnage](../profiling/lines-view-dotnet-memory-sampling-data.md)  
 Répertorie les données d’allocation de mémoire des lignes de code source lors de l’exécution du profilage.  
  
 [Vue Pointeurs d’instruction (IP) - Échantillonnage](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)  
 Répertorie les données d’allocation de mémoire des instructions de fonctions lors de l’exécution du profilage.  
  
 [Vue Arborescence des appels - Instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)  
 Affiche une arborescence hiérarchique qui représente les chemins d’exécution, les données d’allocation de mémoire et les données de minutage détaillées des fonctions instrumentées de l’exécution du profilage.  
  
 [Vue Modules - Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)  
 Organise les données de profilage par module et répertorie les fonctions, les données d’allocation de mémoire et les données de minutage détaillées du module.  
  
 [Vue Appelant/Appelé - Données d’instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)  
 Répertorie les données d’allocation de mémoire et les données de minutage détaillées d’une fonction instrumentée sélectionnée, ainsi que les fonctions qui ont appelé la fonction sélectionnée et les fonctions qui ont été appelées par la fonction sélectionnée.  
  
 [Vue Fonctions - Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)  
 Répertorie les données d’allocation de mémoire des fonctions instrumentées lors de l’exécution du profilage.  
  
## <a name="reference"></a>Référence  
 [Vue Informations relatives à la fonction](../profiling/function-details-view.md)  
 Affiche un graphique de la relation qui existe entre une fonction sélectionnée et les fonctions qui l’ont appelée et qui ont été appelées par celle-ci.  
  
 [Vue Processus](../profiling/process-view.md)  
 Répertorie les heures de début et de fin des processus et des threads.  
  
 [Vue Marques](../profiling/marks-view.md)  
 Répertorie les événements ETW et les événements d’échantillonnage insérés dans un fichier de données de profilage.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)  
 Informations de référence sur les vues et les rapports des fichiers de données du profileur générés à l’aide de la méthode d’échantillonnage.  
  
 [Vues de données de la méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)  
 Informations de référence sur les vues et les rapports des fichiers de données du profileur générés à l’aide de la méthode d’instrumentation.