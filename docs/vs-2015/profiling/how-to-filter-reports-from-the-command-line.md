---
title: Guide pratique pour filtrer des rapports à partir de la ligne de commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db2c9d845af962fc17da1ebd84e8dd5fe6ffadab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146004"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Comment : filtrer des rapports à partir de la ligne de commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En utilisant les options de la commande **VSPerfReport**, vous pouvez filtrer des rapports sur un segment de temps spécifique du fichier de données de profilage, ou restreindre les données à un ou plusieurs processus ou threads. Pour plus d’informations sur cette commande, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
|Options|Description|  
|-------------|-----------------|  
|**StartTime:**[*Valeur*]|Affiche uniquement les données collectées après la valeur (en millisecondes).|  
|**EndTime:**[*Valeur*]|Affiche uniquement les données collectées avant la valeur (en millisecondes).|  
|**FilterFile:** `VSPFFile`|Spécifie l’emplacement d’un fichier de filtre qui a été généré à partir de la fenêtre **Rapport de performances de Visual Studio**.|  
|**MsFilter:**[*StartTime,Duration*]|Affiche uniquement les données de `StartTime` jusqu’à la fin de `Duration` (en millisecondes).|  
|**Process:**[*Pid*]|Affiche uniquement les données du processus spécifié.|  
|**Thread:**[*ThreadID*]|Affiche uniquement les données du thread spécifié.|  
|**Thread:**[*ThreadID,ProcessID*]|Affiche uniquement les données du thread spécifié qui est associé au processus spécifié.|
