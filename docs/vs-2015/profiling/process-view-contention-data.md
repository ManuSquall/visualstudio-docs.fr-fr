---
title: Processus, vue - Données de conflit | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 411de842beb616cf4ed7c51d0458e8d7bce82690
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502990"
---
# <a name="process-view---contention-data"></a>Processus, vue - Données de conflit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue processus - données de conflit](https://docs.microsoft.com/visualstudio/profiling/process-view-contention-data).  
  
La vue Processus affiche les données de conflit pour les processus et les threads exécutés pendant l’exécution du profilage.  
  
 Quand des symboles sont disponibles, les processus sont répertoriés par nom. Si aucun symbole n’est disponible, les processus sont répertoriés par adresse mémoire, au format hexadécimal. Les threads sont répertoriés en tant qu’enfants du processus qui les a créés.  
  
 Le tableau suivant explique les valeurs des colonnes dans la vue Processus.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Heure de début**|Nombre de millisecondes ou de cycles processeur entre le début du profilage et le début du processus ou du thread.|  
|**Temps bloqué**|Durée totale pendant laquelle l’exécution des fonctions du processus ou du thread a été bloquée.|  
|**% de temps bloqué**|Pourcentage de la durée de vie du processus ou du thread pendant laquelle l’exécution des fonctions du processus ou du thread a été bloquée.|  
|**Conflits**|Nombre de fois où l’exécution des fonctions du processus ou du thread a été bloquée.|  
|**% de conflits**|Pourcentage de tous les conflits dans l’exécution du profilage qui étaient des conflits du processus ou du thread.|  
|**Heure de fin**|Nombre de millisecondes ou de cycles processeur entre le début du profilage et la fin du processus ou du thread.|  
|**ID**|Identificateur du processus ou du thread généré par le système.|  
|**Durée de vie**|Nombre de millisecondes ou de cycles processeur entre le début du processus ou du thread et soit la fin du processus ou du thread, soit la fin du profilage.|  
|**Type**|Type de ligne (processus ou thread).<br /><br /> Uniquement dans les rapports en ligne de commande **VSReport**. Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).|  
|**Name**|Nom du processus ou du thread.|  
|**ID unique**|Identificateur généré par le profileur unique pour le processus ou le thread.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Processus, vue](../profiling/process-view.md)



