---
title: Vue Appelant/Appelé - Données d’échantillonnage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f5e3c28d7aa24f46bb3fc09045574030f8eb03db
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54803921"
---
# <a name="caller--callee-view---sampling-data"></a>Vue Appelant/Appelé - Données d’échantillonnage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue Appelant/Appelé affiche des données de profilage pour la fonction sélectionnée, ainsi que pour ses fonctions parents et enfants. La vue Appelant/Appelé comprend trois grilles.  
  
 La grille centrale intitulée **Fonction active** contient les informations de profilage associées à la fonction sélectionnée. Ces valeurs incluent tous les appels échantillonnés émis vers la fonction.  
  
 La grille supérieure intitulée **Fonctions qui ont appelé la fonction active** contient les contributions de chaque fonction d’appelant (parent) aux valeurs de la fonction sélectionnée (active).  
  
 La grille inférieure intitulée **Fonctions qui ont été appelées par la fonction active** contient des informations de profilage pour les fonctions d’appelé (enfants) de la fonction sélectionnée lorsque la fonction enfant a été appelée par la fonction active.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
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
|**Type**|Contexte de la fonction :<br /><br /> -   **0** : fonction active<br />-   **1** : fonction qui appelle la fonction active<br />-   **2** : fonction qui est appelée par la fonction active|  
|**Nom de fonction racine**|Nom de la fonction active.|  
|**Échantillons inclusifs**|- Pour la fonction active, nombre d’échantillons collectés malgré l’exécution de cette fonction ou de l’une de ses fonctions enfants.<br />- Pour une fonction d’appelant, nombre d’échantillons inclusifs de la fonction active qui ont été collectés lorsque cette fonction a appelé la fonction active.<br />- Pour une fonction d’appelé, nombre d’échantillons inclusifs de cette fonction qui ont été collectés lorsque la fonction active a appelé cette fonction.|  
|**% des échantillons inclusifs**|Pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons inclusifs de cette fonction.|  
|**Échantillons exclusifs**|- Pour la fonction active, nombre d’échantillons de l’exécution du profilage qui ont été collectés pendant l’exécution directe de cette fonction ; autrement dit, lorsque cette fonction se trouvait en haut de la pile des appels. Les échantillons collectés lors de l’exécution des fonctions enfants de cette fonction ne sont pas comptabilisés comme des échantillons exclusifs.<br />- Pour une fonction d’appelant, nombre d’échantillons exclusifs de la fonction active qui ont été collectés lorsque cette fonction a appelé la fonction active.<br />- Pour une fonction d’appelé, nombre d’échantillons exclusifs de cette fonction qui ont été collectés lorsque la fonction active a appelé cette fonction.|  
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons exclusifs de cette fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Appelant/Appelé - Données d’échantillonnage de mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vue Appelant/Appelé - Données d’instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Vue Appelant/Appelé - Données d’instrumentation](../profiling/caller-callee-view-instrumentation-data.md)
