---
title: "Fonctionnement des valeurs de données d’instrumentation | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7f0fc8530e45831132f3ec3f357ff0113fa4abe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="understanding-instrumentation-data-values"></a>Fonctionnement des valeurs de données d’instrumentation
La méthode de profilage par *instrumentation* de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enregistre les informations de minutage détaillées pour les appels de fonction, les lignes et les instructions de l’application profilée.  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 La méthode par instrumentation injecte le code au début et de fin de fonctions cibles dans le fichier binaire profilé, et avant et après chaque appel d’autres fonctions par ces fonctions. Le code injecté enregistre les informations suivantes :  
  
-   L’intervalle entre cet événement de collecte et le précédent.  
  
-   Si le système d’exploitation a effectué une opération pendant l’intervalle. Par exemple, le système d’exploitation peut lire ou écrire sur un disque, ou basculer entre le thread cible et un autre thread d’un autre processus.  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Pour chaque intervalle, l’analyse du profileur reconstruit la pile des appels qui était présente à la fin de l’intervalle. Une pile des appels est la liste des fonctions qui sont actives sur un processeur à un point dans le temps. Une seule fonction (la fonction active) exécute du code ; les autres fonctions sont la chaîne des appels de fonction qui a provoqué l’appel à la fonction active (la pile des appels).  
  
 Pour chaque fonction présente sur la pile des appels quand l’intervalle a été enregistré, l’analyse du profileur ajoute l’intervalle à une ou plusieurs parmi quatre valeurs de données pour la fonction. L’analyse ajoute l’intervalle à une valeur de données pour une fonction selon deux critères :  
  
-   Si l’intervalle s’est produit dans le code de la fonction ou dans une *fonction enfant* (une fonction qui a été appelée par la fonction).  
  
-   Si un événement du système d’exploitation s’est produit dans l’intervalle.  
  
 Les valeurs de données pour un intervalle d’une fonction ou une plage de données sont nommées *Inclusif écoulé*, *Exclusif écoulé*, *Inclusif d’application* et *Exclusif d’application* :  
  
-   Tous les intervalles d’une fonction sont ajoutés à la valeur de données Inclusif écoulé.  
  
-   Si l’intervalle s’est produit dans le code de la fonction et pas dans une fonction enfant, l’intervalle est ajouté à la valeur de données Exclusif écoulé de la fonction.  
  
-   Si aucun événement du système d’exploitation ne s’est produit dans l’intervalle, l’intervalle est ajouté à la valeur de données Inclusif d’application.  
  
-   Si aucun événement du système d’exploitation ne s’est produit dans l’intervalle et que l’intervalle s’est produit dans l’exécution directe du code de la fonction (autrement dit, il ne s’est pas produit dans une fonction enfant), l’intervalle est ajouté à la valeur de données Exclusif d’application.  
  
 Les rapports des outils de profilage agrègent les valeurs totales des fonctions dans la session de profilage elle-même, des processus, des threads et des fichiers binaires de la session.  
  
## <a name="elapsed-inclusive-values"></a>Valeurs de temps inclusif écoulé  
 Temps total passé à exécuter une fonction et ses fonctions enfants.  
  
 Les valeurs de temps inclusif écoulé incluent les intervalles passés à exécuter directement le code de la fonction et les intervalles passés à exécuter les fonctions enfants de la fonction cible. Les intervalles de la fonction ou de ses fonctions enfants qui incluent une attente du système d’exploitation sont également inclus dans les valeurs Inclusif écoulé.  
  
## <a name="elapsed-exclusive-values"></a>Valeurs de temps exclusif écoulé  
 Temps passé à exécuter une fonction, à l’exclusion du temps passé dans les fonctions enfants.  
  
 Les valeurs de temps exclusifs écoulé incluent les intervalles passés directement à l’exécution du code de la fonction, indépendamment de la survenance ou non d’un événement du système d’exploitation dans l’intervalle. Tous les intervalles passés dans les fonctions enfants qui ont été appelées par la fonction cible ne sont pas inclus dans les valeurs de temps exclusif écoulé.  
  
## <a name="application-inclusive-values"></a>Valeurs de temps inclusif d’application  
 Temps passé à exécuter une fonction et ses fonctions enfants, à l’exclusion du temps passé dans les événements du système d’exploitation.  
  
 Les valeurs de temps inclusif d’application n’incluent pas les intervalles qui contiennent des événements du système d’exploitation. Elles incluent tous les autres intervalles consacrés passés à exécuter une fonction, que l’intervalle ait été passé directement à exécuter le code de la fonction ou à exécuter le code des fonctions enfants de la fonction cible.  
  
## <a name="application-exclusive-values"></a>Valeurs de temps exclusif d’application  
 Temps passé à exécuter une fonction, à l’exclusion du temps passé dans les fonctions enfants et dans les événements du système d’exploitation.  
  
 Les valeurs de temps exclusives d’application n’incluent pas les intervalles qui contiennent des événements du système d’exploitation ou ni les intervalles consacrés à l’exécution des fonctions appelées par la fonction. Elles incluent seulement les intervalles consacrés directement à l’exécution du code de la fonction et qui ne contenaient pas d’événement du système d’exploitation.  
  
## <a name="elapsed-inclusive-percent"></a>Pourcentage de temps inclusif écoulé  
 Pourcentage du total des valeurs de temps inclusif écoulé de la session de profilage qui étaient des valeurs de temps inclusif écoulé de la fonction, du module, du thread ou du processus.  
  
 100 * Temps inclusif écoulé de la fonction / Temps inclusif écoulé de la session  
  
## <a name="elapsed-exclusive-percent"></a>Pourcentage de temps exclusif écoulé  
 Pourcentage du total des valeurs de temps inclusif écoulé de la session de profilage qui étaient des valeurs de temps exclusif écoulé de la fonction, du module, du thread ou du processus.  
  
 100 * Temps exclusif écoulé de la fonction / Temps inclusif écoulé de la session  
  
## <a name="application-inclusive-percent"></a>Pourcentage de temps inclusif d’application  
 Pourcentage du total des valeurs de temps inclusif d’application de la session de profilage qui étaient des valeurs de temps inclusif d’application de la fonction, du module, du thread ou du processus.  
  
 100 * Temps inclusif d’application de la fonction / Temps inclusif d’application de la session  
  
## <a name="application-exclusive-percent"></a>Pourcentage de temps exclusif d’application  
 Pourcentage du total des valeurs de temps inclusif d’application de la session de profilage qui étaient des intervalles de temps exclusif d’application de la fonction, du module, du thread ou du processus.  
  
 100 * Temps exclusif d’application de la fonction / Temps inclusif d’application de la session  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse des données des outils d’analyse des performances](../profiling/analyzing-performance-tools-data.md)   
 [Guide pratique pour choisir des méthodes de collecte](../profiling/how-to-choose-collection-methods.md)