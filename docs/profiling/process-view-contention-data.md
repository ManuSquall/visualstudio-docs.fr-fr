---
title: "Vue Processus - donn&#233;es de conflit du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Processus (vue)"
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Vue Processus - donn&#233;es de conflit du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Processus affiche les données de conflit pour les processus et les threads exécutés pendant le profilage.  
  
 Lorsque des symboles sont disponibles, les processus sont répertoriés par nom.  Si aucun symbole n'est disponible, les processus sont répertoriés par adresse mémoire, au format hexadécimal.  Les threads sont répertoriés en tant qu'enfants du processus qui les a créés.  
  
 Le tableau suivant explique les valeurs des colonnes dans la table de vue Processus.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Heure de début**|Nombre de millisecondes ou de cycles processeur entre le démarrage du profileur et le démarrage du processus ou du thread.|  
|**Temps bloqué**|Durée totale pendant laquelle les fonctions du processus ou du thread ont été bloquées.|  
|**% de temps bloqué**|Pourcentage de la durée de vie du processus ou du thread pendant laquelle les fonctions du processus ou du thread ont été bloquées.|  
|**Conflits**|Nombre de fois que les fonctions du processus ou du thread ont été bloquées.|  
|**% de conflits**|Pourcentage de tous les conflits dans l'exécution du profilage qui étaient des conflits de processus ou de thread.|  
|**Heure de fin**|Nombre de millisecondes ou de cycles processeur entre le démarrage du profileur et la fin du processus ou du thread.|  
|**ID**|Identificateur de processus ou de thread généré par le système.|  
|**Durée de vie**|Nombre de millisecondes ou de cycles processeur entre le démarrage du processus ou du thread  et la fin du processus ou du thread ou la fin du profilage.|  
|**Type**|Type de ligne, processus ou thread.<br /><br /> Uniquement dans les rapports en ligne de commande **VSReport**.  Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).|  
|**Name**|Nom du processus ou du thread.|  
|**ID unique**|Identificateur généré par le profileur unique pour le processus ou le thread.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Mode Processus](../profiling/process-view.md)