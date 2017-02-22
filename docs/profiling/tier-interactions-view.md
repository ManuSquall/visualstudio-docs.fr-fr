---
title: "Interactions de couche, vue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.tierinteraction"
helpviewer_keywords: 
  - "Interactions de couche (vue)"
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Interactions de couche, vue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le profilage des interactions de couche fournit des informations supplémentaires sur les temps d'exécution des fonctions dans les applications multicouches qui communiquent avec les bases de données via [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)].  Les données sont collectées uniquement pour les appels de fonction synchrones.  
  
 **Configuration requise**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]  
  
 La vue Interactions affiche les données d'interactions de couche dans deux volets :  
  
-   Le volet principal est une arborescence hiérarchique.  La ligne supérieure contient les données agrégées pour les connexions de base de données d'un processus ou d'une page [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Les nœuds enfants contiennent des données agrégées pour les connexions de base de données du parent.  
  
-   Lorsque vous cliquez sur un nœud d'appel base de données dans le volet principal, les données de l'instance de l'appel de base de données sont affichées dans le volet d'informations.  
  
 Le temps est affiché en nombre de millisecondes ou en nombre de battements d'horloge de l'unité centrale.  Pour modifier l'unité de temps affichée, cliquez sur le menu **Outils**, cliquez sur **Options**, puis choisissez l'une des options **Afficher valeurs d'heure comme**.  
  
## Volet principal  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Name**|-   Pour une ligne supérieure, nom du processus profilé ou page Web.<br />-   Pour une ligne de connexion de base de données, nom du serveur qui héberge la base de données.|  
|**Base de données**|Nom de la base de données \(lignes de connexion de base de données uniquement\).|  
|**Count**|Nombre total de requêtes générées par le processus, la page Web ou la connexion de base de données.|  
|**Temps total écoulé**|Durée totale passée à exécuter une requête à partir du processus, de la page Web ou de la connexion de base de données.|  
|**Temps écoulé max.**|Durée maximale passée à exécuter une requête à partir du processus, de la page Web ou de la connexion de base de données.|  
|**Temps écoulé min.**|Durée minimale passée à exécuter une requête à partir du processus, de la page Web ou de la connexion de base de données.|  
|**Temps moyen écoulé**|Durée moyenne passée à exécuter une requête à partir du processus, de la page Web ou de la connexion de base de données.|  
  
## Volet d'informations Connexion de base de données  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Texte de la commande**|Requête SQL de la demande.|  
|**Nombre de requêtes**|Nombre d'exécutions de la requête.|  
|**Temps total écoulé**|Durée totale passée à exécuter les instances de la requête.|  
|**Temps écoulé max.**|Durée maximale passée à exécuter une instance de la requête.|  
|**Temps écoulé min.**|Durée minimale passée à exécuter une instance de la requête.|  
|**Temps moyen écoulé**|Durée moyenne passée à exécuter une instance de la requête.|