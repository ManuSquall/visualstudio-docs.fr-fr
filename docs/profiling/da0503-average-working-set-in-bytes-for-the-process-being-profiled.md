---
title: "DA0503&#160;: jeu de travail moyen, en octets, pour le processus en cours de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.503"
  - "vs.performance.DA0503"
  - "vs.performance.rules.DA0503"
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DA0503&#160;: jeu de travail moyen, en octets, pour le processus en cours de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0503|  
|Catégorie|Analyse de ressource|  
|Méthode de profilage|Tous|  
|Message|Ces informations ont été rassemblées à titre d'information uniquement.  Le compteur Traiter le jeu de travail mesure l'utilisation de la mémoire physique par le processus en cours de profilage.  La valeur signalée correspond à la moyenne pour tous les intervalles de mesure.|  
|Type de règle|Information|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## Description de la règle  
 Ce message signale la quantité moyenne de mémoire physique que le processus utilise actuellement en octets \(jeu de travail\).  La plage de travail du processus représente des pages de l'espace d'adressage du processus qui résident actuellement dans la mémoire physique.  
  
 La valeur signalée inclut des pages résidantes provenant de segments de mémoire partagée que le processus a référencés.  Les DLL partagées que le processus référence sont incluses dans les segments de mémoire partagée comptés.  La valeur du jeu de travail du processus peut être plus élevée que la quantité de mémoire virtuelle allouée par le processus en raison des segments de mémoire partagée.  
  
 La valeur signalée est la moyenne de tous les intervalles de mesure dans lesquels le processus profilé était actif.  
  
 La taille du jeu de travail du processus reflète la quantité de mémoire virtuelle que le processus utilise activement.  Elle est également affectée par la quantité de mémoire physique \(ou RAM\) disponible pour exécuter l'application et le conflit pour cette mémoire physique à partir d'autres processus en cours d'exécution.  Si la mémoire physique est contrainte, la valeur du jeu de travail du processus peut varier considérablement lorsque le système d'exploitation essaie d'équilibrer l'utilisation de la mémoire à travers des processus actifs en ajustant périodiquement les pages relativement inactives à partir des jeux de travail du processus.  
  
 Pour plus d'informations sur les plages de travail du processus, consultez [Plage de travail](http://go.microsoft.com/fwlink/?LinkId=177830) dans la documentation de gestion de la mémoire Windows MSDN.  
  
## Comment utiliser des données de règle  
 Utilisez la valeur de règle pour comparer les performances de différentes versions du programme ou pour comprendre les performances de l'application selon des scénarios de profilage différents.  
  
 Double\-cliquez sur le message dans la fenêtre Liste d'erreurs pour naviguer jusqu'à la [vue Marques](../profiling/marks-view.md) des données de profilage.  Recherchez les colonnes **Processus\\Jeu de travail** et **Mémoire\\Pages\/s**.  Comparez les deux colonnes et déterminez s'il existe des phases spécifiques d'exécution du programme qui semblent être associées à une activité d'E\/S de pagination accrue.