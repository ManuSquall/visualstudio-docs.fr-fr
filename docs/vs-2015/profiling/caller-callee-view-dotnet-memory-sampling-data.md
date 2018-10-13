---
title: Vue Appelant/Appelé - Données d’échantillonnage de mémoire .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85aaa285a190ae1167a86b32583d4349f3a78d56
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243046"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Vue Appelant/Appelé - Données d’échantillonnage de mémoire .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue Appelant/Appelé affiche des données de profilage de mémoire .NET pour la fonction sélectionnée, ainsi que pour ses fonctions parents et enfants. La vue Appelant/Appelé comprend trois grilles.  
  
 La grille centrale intitulée **Fonction active** contient les informations de profilage de mémoire associées à la fonction sélectionnée. Ces valeurs incluent tous les appels échantillonnés émis vers la fonction.  
  
 La grille supérieure intitulée **Fonctions qui ont appelé la fonction active** indique la valeur de la fonction sélectionnée (active) qui a été générée par les appels de la fonction d’appelant (parent).  
  
 La grille inférieure intitulée **Fonctions qui ont été appelées par la fonction active** contient les données de profilage de mémoire pour les fonctions d’appelé (enfants) de la fonction sélectionnée lorsque la fonction enfant a été appelée par la fonction active.  
  
 Double-cliquez sur la ligne d’une fonction d’appelant ou d’appelé pour en faire la fonction active.  
  
|Colonne|Description|  
|------------|-----------------|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom du module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|  
|**Nom de la fonction**|Nom complet de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Type**|Contexte de la fonction :<br /><br /> **0** : la fonction active.<br /><br /> **1** : fonction qui appelle la fonction active<br /><br /> **2** : fonction qui est appelée par la fonction active<br /><br /> Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
|**Niveau**|Profondeur de la fonction dans l’arborescence des appels. Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
|**Allocations inclusives**|- Pour la fonction active, nombre d’objets alloués par la fonction dans l’exécution du profilage. Ce nombre comprend les objets créés dans les fonctions d’appelé.<br />- Pour une fonction d’appelant, nombre d’allocations inclusives de la fonction active qui ont été générées par les appels émis à partir de cette fonction.<br />- Pour une fonction d’appelé, nombre d’objets alloués par les instances de cette fonction qui ont été appelées par la fonction active. Ce nombre comprend les allocations effectuées par les fonctions qui ont été appelées par la fonction d’appelé.|  
|**% d’allocations inclusives**|Pourcentage de tous les objets créés lors de l’exécution du profilage qui étaient des allocations inclusives de cette fonction.|  
|**Allocations exclusives**|- Pour la fonction active, nombre d’objets créés lorsque la fonction exécutait le code du corps de la fonction (autrement dit, lorsque la fonction se trouvait en haut de la pile des appels). Ce nombre n’inclut pas les objets créés dans les fonctions appelées par cette fonction.<br />- Pour une fonction d’appelant, nombre d’allocations exclusives de la fonction active qui ont été générées par les appels émis à partir de cette fonction.<br />- Pour une fonction d’appelé, nombre d’objets créés par les instances de cette fonction qui ont été appelées par la fonction active. Ce nombre n’inclut pas les objets créés par les fonctions appelées par la fonction d’appelé.|  
|**% d’allocations exclusives**|Pourcentage de tous les objets créés lors de l’exécution du profilage qui étaient des allocations inclusives de cette fonction.|  
|**Octets inclusifs**|- Pour la fonction active, nombre d’octets de mémoire alloués par la fonction dans l’exécution du profilage. Ce nombre comprend la mémoire allouée dans les fonctions qui ont été appelées par cette fonction.<br />- Pour une fonction d’appelant, nombre d’octets inclusifs de la fonction active qui ont été générés par les appels émis par la fonction d’appelant.<br />- Pour une fonction d’appelé, nombre d’octets alloués par les instances de cette fonction qui ont été générées par les appels émis par la fonction active. Ce nombre comprend les octets alloués par les fonctions qui ont été appelées par la fonction d’appelé.|  
|**% d’octets inclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage qui étaient des allocations inclusives de cette fonction.|  
|**Octets exclusifs**|- Pour la fonction active, nombre d’octets de mémoire alloués par la fonction dans l’exécution du profilage. Ce nombre n’inclut pas la mémoire allouée par les fonctions qui ont été appelées par la fonction active.<br />- Pour une fonction d’appelant, nombre d’octets exclusifs de la fonction active qui ont été générés par les appels émis par la fonction d’appelant.<br />- Pour une fonction d’appelé, nombre d’octets alloués par les instances de cette fonction qui ont été générées par les appels émis par la fonction active. Ce nombre ne comprend pas les octets alloués par les fonctions qui ont été appelées par la fonction d’appelé.|  
|**% d’octets exclusifs**|Pourcentage de tous les octets de mémoire alloués lors de l’exécution du profilage qui étaient des allocations exclusives de cette fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Vue Appelant/Appelé - Données d’instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Vue Appelant/Appelé - Données d’échantillonnage](../profiling/caller-callee-view-sampling-data.md)   
 [Vue Appelant/appelé - Données d’instrumentation](../profiling/caller-callee-view-instrumentation-data.md)



