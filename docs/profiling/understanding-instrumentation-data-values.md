---
title: "Fonctionnement des valeurs de donn&#233;es d’instrumentation dans des outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils de profilage, instrumentation"
  - "instrumentation, méthode de profilage"
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Fonctionnement des valeurs de donn&#233;es d’instrumentation dans des outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La méthode de profilage par *instrumentation* de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] stocke les informations détaillées de timing pour les appels de fonctions, les lignes, et les instructions dans l'application profilée  
  
 **Configuration requise**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 La méthode d'instrumentation injecte le code au début et à la fin de fonctions cibles dans le fichier binaire profilé, ainsi qu'avant et après chaque appel d'autres fonctions par ces fonctions.  Le code injecté enregistre les éléments suivants :  
  
-   l'intervalle entre cet événement de collecte et le précédent ;  
  
-   si le système d'exploitation a effectué une opération au cours de l'intervalle  \(par exemple, le système d'exploitation peut lire ou écrire sur disque ou commuter entre le thread cible et un autre thread d'un autre processus\).  
  
 **Configuration requise**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Pour chaque intervalle, l'analyse du profileur reconstruit la pile des appels qui était présente à la fin de l'intervalle.  Une pile des appels est la liste des fonctions qui sont actives sur un processeur à un moment donné.  Une seule fonction \(la fonction active\) exécute le code ; les autres fonctions représentent la chaîne des appels de fonction qui ont provoqué l'appel de la fonction active \(la pile des appels\).  
  
 Pour chaque fonction de la pile des appels présente à l'enregistrement de l'intervalle, l'analyse du profileur ajoute l'intervalle à une ou plusieurs valeurs de données \(parmi quatre\) pour la fonction.  L'analyse ajoute l'intervalle à une valeur de données pour une fonction en fonction de deux critères :  
  
-   si l'intervalle s'est produit dans le code de la fonction ou dans une *fonction enfant* \(une fonction appelée par la fonction\) ;  
  
-   si un événement du système d'exploitation s'est produit dans l'intervalle.  
  
 Les valeurs de données pour un intervalle d'une fonction ou une plage de données sont de quatre types : *Inclusif écoulé*, *Exclusif écoulé*, *Inclusif d'application* et *Exclusif d'application* :  
  
-   Tous les intervalles d'une fonction sont ajoutés à la valeur de données de type Inclusif écoulé.  
  
-   Si l'intervalle s'est produit dans le code de la fonction et non dans une fonction enfant, il est ajouté à la valeur de données Exclusif écoulé de la fonction.  
  
-   Si un événement du système d'exploitation ne s'est pas produit dans l'intervalle, celui\-ci est ajouté à la valeur de données Inclusif d'application.  
  
-   Si un événement du système d'exploitation ne s'est pas produit dans l'intervalle et que celui\-ci s'est produit lors de l'exécution directe du code de fonction \(autrement dit, il ne s'est pas produit dans une fonction enfant\), l'intervalle est ajouté à la valeur de données Exclusif d'application.  
  
 Les rapports des outils de profilage regroupent les valeurs totales des fonctions dans la session de profilage proprement dite ainsi que dans les processus, threads et binaires de la session.  
  
## Valeurs de type Inclusif écoulé  
 Durée totale d'exécution d'une fonction et de ses fonctions enfants.  
  
 Les valeurs Inclusif écoulé incluent les intervalles liés directement à l'exécution du code de fonction et ceux liés à l'exécution des fonctions enfants de la fonction cible.  Les intervalles de la fonction ou de ses fonctions enfants qui sont en attente du système d'exploitation sont également inclus dans les valeurs Inclusif écoulé.  
  
## Valeurs de type Exclusif écoulé  
 Durée d'exécution d'une fonction, à l'exclusion de la durée d'exécution des fonctions enfants.  
  
 Les valeurs de type Exclusif écoulé incluent les intervalles liés directement à l'exécution du code de fonction, qu'un événement du système d'exploitation se soit produit ou non dans l'intervalle.  Tous les intervalles liés aux fonctions enfants appelées par la fonction cible ne sont pas inclus dans les valeurs Exclusif écoulé.  
  
## Valeurs de type Inclusif d'application  
 Durée d'exécution d'une fonction et de ses fonctions enfants, à l'exclusion de la durée des événements du système d'exploitation.  
  
 Les valeurs de type Inclusif d'application n'incluent pas les intervalles qui contiennent des événements du système d'exploitation.  Elles incluent tous les autres intervalles liés à l'exécution d'une fonction, que l'intervalle soit lié directement à l'exécution du code de fonction ou aux fonctions enfants de la fonction cible.  
  
## Valeurs de type Exclusif d'application  
 Durée d'exécution d'une fonction, à l'exclusion de la durée consacrée aux fonctions enfants et aux événements du système d'exploitation.  
  
 Les valeurs de type Exclusif d'application n'incluent pas les intervalles qui contiennent les événements du système d'exploitation, ni les intervalles consacrés à l'exécution des fonctions appelées par la fonction.  Elles incluent uniquement les intervalles consacrés directement à l'exécution du code de fonction et qui ne contiennent aucun événement du système d'exploitation.  
  
## Pourcentage de type Inclusif écoulé  
 Pourcentage du total des valeurs Inclusif écoulé de la session de profilage qui étaient des valeurs Inclusif écoulé de la fonction, du module, du thread ou du processus.  
  
 100 \* Inclusif écoulé de la fonction \/ Inclusif écoulé de la session  
  
## Pourcentage de type Exclusif écoulé  
 Pourcentage du total des valeurs Inclusif écoulé de la session de profilage qui étaient des valeurs Exclusif écoulé de la fonction, du module, du thread ou du processus.  
  
 100 \* Exclusif écoulé de la fonction \/ Inclusif écoulé de la session  
  
## Pourcentage de type Inclusif d'application  
 Pourcentage du total des valeurs Inclusif d'application de la session de profilage qui étaient des valeurs Inclusif d'application de la fonction, du module, du thread ou du processus.  
  
 100 \* Inclusif d'application de la fonction \/ Inclusif d'application de la session  
  
## Pourcentage de type Exclusif d'application  
 Pourcentage du total des valeurs Inclusif d'application de la session de profilage qui étaient des intervalles Exclusif d'application de la fonction, du module, du thread ou du processus.  
  
 100 \* Exclusif d'application de la fonction \/ Inclusif d'application de la session  
  
## Voir aussi  
 [Analyse des données des outils de profilage](../profiling/analyzing-performance-tools-data.md)   
 [Comment : choisir des méthodes de collection](../profiling/how-to-choose-collection-methods.md)