---
title: Vue Interaction de couche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a3bf4f5fd7ab18efb13e1c52847daf647e908b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968774"
---
# <a name="tier-interactions-view"></a>Interactions de couche, vue

Le profilage d’interaction de couche fournit des informations supplémentaires sur les temps d’exécution des fonctions des applications multicouches qui communiquent avec des bases de données via [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]. Les données sont collectées uniquement pour les appels de fonctions synchrones.

**Spécifications**

- Visual Studio Enterprise

La vue Interactions affiche les données d’interaction de couche dans deux volets :

- Le volet principal est une arborescence hiérarchique. La ligne de plus haut niveau contient les données agrégées pour les connexions de base de données d’une page [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ou d’un processus. Les nœuds enfants contiennent des données agrégées pour les connexions de base de données du parent.

- Quand vous cliquez sur un nœud d’appel de base de données dans le volet principal, les données de l’instance de l’appel de base de données s’affichent dans le volet des détails.

  La durée affichée correspond au nombre de millisecondes ou au nombre de cycles d’horloge de l’UC. Pour modifier l’unité d’affichage de la durée, cliquez sur le menu **Outils**, cliquez sur **Options** puis choisissez une des options de **Afficher les valeurs de date/heure comme**.

## <a name="master-pane"></a>Volet principal

|Colonne|Description|
|------------|-----------------|
|**Name**|- Pour une ligne de haut niveau, le nom de la page web ou du processus profilé.<br />- Pour une ligne de connexion de base de données, le nom du serveur qui héberge la base de données.|
|**Base de données**|Nom de la base de données (lignes de connexion de base de données uniquement).|
|**Nombre**|Nombre total de demandes qui sont générées par le processus, une page web ou une connexion de base de données.|
|**Temps écoulé total**|Temps total passé dans l’exécution d’une demande provenant du processus, de la page web ou de la connexion de base de données.|
|**Temps écoulé max.**|Temps maximal passé dans l’exécution d’une demande provenant du processus, de la page web ou de la connexion de base de données.|
|**Temps écoulé min.**|Temps minimal passé dans l’exécution d’une demande provenant du processus, de la page web ou de la connexion de base de données.|
|**Temps moyen écoulé**|Temps moyen passé dans l’exécution d’une demande provenant du processus, de la page web ou de la connexion de base de données.|

## <a name="database-connection-details-pane"></a>Volet d’informations de connexion de base de données

|Colonne|Description|
|------------|-----------------|
|**Texte de la commande**|Requête SQL de la demande.|
|**Nombre de requêtes**|Nombre d’exécutions de la requête.|
|**Temps écoulé total**|Temps total passé à exécuter les instances de la requête.|
|**Temps écoulé max.**|Temps maximal passé à exécuter une des instances de la requête.|
|**Temps écoulé min.**|Temps minimal passé à exécuter une des instances de la requête.|
|**Temps moyen écoulé**|Temps moyen passé à exécuter une instance de la requête.|