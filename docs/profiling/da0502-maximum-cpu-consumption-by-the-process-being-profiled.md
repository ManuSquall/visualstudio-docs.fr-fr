---
title: "DA0502&#160;: consommation processeur maximale par le processus en cours de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0502"
  - "vs.performance.DA0502"
  - "vs.performance.502"
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DA0502&#160;: consommation processeur maximale par le processus en cours de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0502|  
|Catégorie|Analyse de ressource|  
|Méthode de profilage|Tous|  
|Message|Règle uniquement pour informations.  Le compteur Processus\(\)\\% temps processus mesure la consommation CPU du processus que vous profilez.  La valeur signalée correspond au maximum observé pour tous les intervalles de mesure.|  
|Type de règle|Informations|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## Description de la règle  
 Ce message signale le pourcentage maximal de temps pendant lequel un processeur était occupé à exécuter des instructions à partir de l'application.  La valeur signalée est la valeur maximale de tous les intervalles de mesure dans lesquels le processus profilé était actif.  Le pourcentage peut être supérieur à 100 % sur un ordinateur doté de plusieurs processeurs.  
  
## Comment utiliser les données de règle  
 Utilisez la valeur de règle pour comparer les performances de différentes versions du programme ou pour comprendre les performances de l'application selon des scénarios de profilage différents.