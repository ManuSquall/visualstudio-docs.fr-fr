---
title: "DA0504&#160;: jeu de travail maximal, en octets, pour le processus en cours de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0504"
  - "vs.performance.504"
  - "vs.performance.rules.DA0504"
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# DA0504&#160;: jeu de travail maximal, en octets, pour le processus en cours de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0504|  
|Catégorie|Gestion des ressources|  
|Méthode de profilage|Tous|  
|Message|Ces informations ont été rassemblées à titre d'information uniquement.  Le compteur Traiter le jeu de travail mesure l'utilisation de la mémoire physique par le processus en cours de profilage.  La valeur signalée est la valeur maximale observée parmi tous les intervalles de mesure.|  
|Type de règle|Information|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## Description de la règle  
 Ce message signale la quantité maximale de mémoire physique, en octets, que le processus utilise actuellement.  La plage de travail du processus représente des pages de l'espace d'adressage du processus qui résident actuellement dans la mémoire physique.  Cette règle signale la valeur maximale pour le jeu de travail du processus lorsque le profilage était actif.  
  
 La valeur signalée inclut des pages résidantes provenant de segments de mémoire partagée que le processus a référencés.  Les DLL partagées que le processus référence sont incluses dans les segments de mémoire partagée comptés.  La valeur du jeu de travail du processus peut être plus élevée que la quantité de mémoire virtuelle allouée par le processus en raison des segments de mémoire partagée.  
  
 La taille du jeu de travail du processus reflète la quantité de mémoire virtuelle que le processus utilise activement.  Elle est également affectée par la quantité de mémoire physique \(ou RAM\) disponible pour exécuter l'application et le conflit pour cette mémoire physique à partir d'autres processus en cours d'exécution.  Pour plus d'informations sur les plages de travail du processus, consultez [Plage de travail](http://go.microsoft.com/fwlink/?LinkId=177830) dans la documentation de gestion de la mémoire Windows MSDN.  
  
## Comment utiliser des données de règle  
 La règle rassemble ces données de mesure à partir de la fonctionnalité de surveillance de performance Windows et les signale uniquement à titre d'information.  Utilisez ces données pour comparer les performances de différentes versions du programme ou pour comprendre les performances de l'application selon des scénarios de test différents.  
  
 Double\-cliquez sur le message dans la fenêtre Liste d'erreurs pour naviguer jusqu'à la [Marques, vue](../profiling/marks-view.md) des données de profilage.  Recherchez les colonnes de compteur **Processus\\Jeu de travail** et **Mémoire\\Pages\/s**.  Recherchez ensuite la valeur maximale de **Processus\\Jeu de travail** et comparez\-la à celle de **Mémoire\\Pages\/s**.  Fréquemment, le jeu de travail maximal est associé à un intervalle dans lequel l'activité d'E\/S de pagination est réduite, surtout si l'ordinateur est limité en mémoire.