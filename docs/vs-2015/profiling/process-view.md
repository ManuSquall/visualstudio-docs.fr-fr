---
title: Vue Processus | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0436401c458a7d6771a2785028a8b5fe0ef57546
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180218"
---
# <a name="process-view"></a>Vue Processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue Processus affiche les données de profilage pour les processus et les threads exécutés pendant l’exécution du profilage.  
  
 Les processus sont répertoriés par nom. Les threads sont répertoriés en tant que nœuds enfants du processus qui les a créés. Les threads sont nommés par la fonction qui a démarré le thread ou par l’étiquette **[ntdll.dll]** si aucun symbole n’est disponible.  
  
 Pour ajouter ou supprimer des colonnes, cliquez avec le bouton droit dans la vue, puis sélectionnez **Ajouter/Supprimer des colonnes**. De plus, vous pouvez trier les données en cliquant sur un nom de colonne. Pour plus d’informations, consultez [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md).  
  
 Les colonnes de la vue Processus sont les mêmes pour les données qui sont générées en utilisant les méthodes d’échantillonnage et d’instrumentation et pour les données qui incluent des données de mémoire .NET. Le tableau suivant décrit les valeurs des colonnes.  
  
|Colonne|Description|  
|------------|-----------------|  
|**ID unique**|Identificateur généré par le profileur unique pour le processus ou le thread.|  
|**Identifiant**|Identificateur du processus ou du thread généré par le système.|  
|**Name**|Nom du processus ou du thread.|  
|**Heure de début**|Nombre de millisecondes ou de cycles processeur entre le début du profilage et le début du processus ou du thread.|  
|**Heure de fin**|Nombre de millisecondes ou de cycles processeur entre le début du profilage et la fin du processus ou du thread.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)   
 [Vues de données de la méthode d’instrumentation](../profiling/instrumentation-method-data-views.md)   
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)
