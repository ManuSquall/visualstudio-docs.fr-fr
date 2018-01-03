---
title: "Explorateur de performances, fenêtre | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords: performance tools, Performance Explorer
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3ab16dca3d4d27c157620f59774ec37f57aae020
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="performance-explorer-window"></a>Explorateur de performances, fenêtre
La fenêtre **Explorateur de performances** de l’environnement de développement intégré (IDE) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous permet de configurer et de démarrer des sessions de performance à l’aide des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 **Spécifications**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## <a name="performance-explorer-toolbar"></a>Barre d’outils de l’Explorateur de performances  
 Vous trouverez les options suivantes dans la barre d’outils de l’**Explorateur de performances** :  
  
-   **Lancer l’Assistant Performance** : affiche l’Assistant Performance qui permet d’ajouter une nouvelle session de performance à la fenêtre Explorateur de performances.  
  
-   **Nouvelle session de performance** : permet d’ajouter une session de performance vide à la fenêtre Explorateur de performances.  
  
-   **Lancer** : la liste du bouton de commande **Lancer** vous permet de démarrer l’application cible dont le profilage est activé immédiatement (**Démarrer avec le profilage**) ou avec le profilage suspendu (**Démarrer avec le profilage suspendu**).  
  
-   **Méthode** : permet de spécifier la méthode de profilage de la session (échantillonnage ou instrumentation).  
  
-   **Arrêter** : permet de quitter immédiatement l’application cible et le profileur.  
  
-   **Attacher/Détacher** : affiche la boîte de dialogue **Attacher le profileur au processus** pour un processus en cours d’exécution auquel attacher le profileur.  
  
## <a name="performance-explorer-window"></a>Fenêtre Explorateur de performances  
 La fenêtre **Explorateur de performances** contient un contrôle d’arborescence qui affiche les fichiers binaires et les fichiers de données des rapports d’une ou de plusieurs sessions de performance.  
  
-   **Nom de la session** : la racine du contrôle d’arborescence contient le nom de la session. Cliquez avec le bouton droit sur le nom de la session pour définir les propriétés de la session ou pour démarrer l’application cible et le profileur.  
  
-   **Cibles** : affiche le nom des fichiers binaires à profiler dans la session. Cliquez avec le bouton droit sur **Cibles** pour ajouter ou supprimer un fichier binaire, un projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou un site web. Cliquez avec le bouton droit sur le nom d’une cible pour définir les propriétés d’un fichier binaire.  
  
-   **Rapports** : affiche le nom des fichiers de données du profileur générés pour la session. Cliquez avec le bouton droit sur **Rapports** pour ajouter un rapport existant ou comparer deux fichiers de données du profileur. Cliquez avec le bouton droit sur le nom d’un rapport pour ouvrir, supprimer ou exporter un fichier de données du profileur.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues d’ensemble](../profiling/overviews-performance-tools.md)   
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Contrôle de la collecte de données](../profiling/controlling-data-collection.md)