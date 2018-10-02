---
title: Vue Interaction de couche | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a0d6753fd852faafcabe291cc9b63ece0fd7752
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504785"
---
# <a name="tier-interactions-view"></a>Interactions de couche (vue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue Interactions de couche](https://docs.microsoft.com/visualstudio/profiling/tier-interactions-view).  
  
Le profilage d’interaction de couche fournit des informations supplémentaires sur les temps d’exécution des fonctions des applications multicouches qui communiquent avec des bases de données via [!INCLUDE[vstecado](../includes/vstecado-md.md)]. Les données sont collectées uniquement pour les appels de fonctions synchrones.  
  
 **Spécifications**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]  
  
 La vue Interactions affiche les données d’interaction de couche dans deux volets :  
  
-   Le volet principal est une arborescence hiérarchique. La ligne de plus haut niveau contient les données agrégées pour les connexions de base de données d’une page [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ou d’un processus. Les nœuds enfants contiennent des données agrégées pour les connexions de base de données du parent.  
  
-   Quand vous cliquez sur un nœud d’appel de base de données dans le volet principal, les données de l’instance de l’appel de base de données s’affichent dans le volet des détails.  
  
 La durée affichée correspond au nombre de millisecondes ou au nombre de cycles d’horloge de l’UC. Pour modifier l’unité d’affichage de la durée, cliquez sur le menu **Outils**, cliquez sur **Options** puis choisissez une des options de **Afficher les valeurs de date/heure comme**.  
  
## <a name="master-pane"></a>Page principale  
  
|Colonne|Description|  
|------------|-----------------|  
|**Name**|-   Pour une ligne du plus haut niveau, le nom du processus ou de la page web profilés.<br />-   Pour une ligne de connexion de base de données, le nom du serveur qui héberge la base de données.|  
|**Base de données**|Nom de la base de données (lignes de connexion de base de données uniquement).|  
|**Nombre**|Nombre total de demandes qui sont générées par le processus, une page web ou une connexion de base de données.|  
|**Temps écoulé total**|Temps total passé dans l’exécution d’une demande provenant du processus, de la page web ou de la connexion de base de données.|  
|**Temps écoulé max.**|Temps maximal passé dans l’exécution d’une demande provenant du processus, de la page web ou de la connexion de base de données.|  
|**Temps écoulé min.**|Temps minimal passé dans l’exécution d’une demande provenant du processus, de la page web ou de la connexion de base de données.|  
|**Temps moyen écoulé**|Temps moyen passé dans l’exécution d’une demande provenant du processus, de la page web ou de la connexion de base de données.|  
  
## <a name="database-connection-details-pane"></a>Volet Informations de connexion de la base de données  
  
|Colonne|Description|  
|------------|-----------------|  
|**Texte de la commande**|Requête SQL de la demande.|  
|**Nombre de requêtes**|Nombre d’exécutions de la requête.|  
|**Temps écoulé total**|Temps total passé à exécuter les instances de la requête.|  
|**Temps écoulé max.**|Temps maximal passé à exécuter une des instances de la requête.|  
|**Temps écoulé min.**|Temps minimal passé à exécuter une des instances de la requête.|  
|**Temps moyen écoulé**|Temps moyen passé à exécuter une instance de la requête.|



