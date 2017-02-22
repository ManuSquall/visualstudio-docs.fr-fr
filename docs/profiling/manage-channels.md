---
title: "G&#233;rer les canaux | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.tools.managechannels"
helpviewer_keywords: 
  - "Visualiseur concurrentiel, gérer les canaux"
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# G&#233;rer les canaux
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans **Vue Threads** dans le Visualiseur concurrentiel, vous pouvez organiser les canaux pour votre processus afin que vous puissiez examiner les modèles particuliers.  Vous pouvez trier les canaux, les déplacer vers le haut et le bas, et les masquer ou les afficher.  
  
## Trier par  
 Vous pouvez utiliser le contrôle Trier par pour trier les threads selon différents critères, en fonction du niveau de zoom actuel.  La possibilité de tri est particulièrement utile lorsque vous recherchez un modèle particulier.  Vous pouvez trier par ces critères :  
  
|Critères|Définition|  
|--------------|----------------|  
|Heure de début|Trie les threads par heures de début.  Il s'agit de l'ordre de tri par défaut.|  
|Heure de fin|Trie les threads par leurs heures de fin.|  
|Exécution|Trie les threads par le pourcentage du temps passé en exécution.|  
|Synchronisation|Trie les threads par le pourcentage du temps passé en synchronisation.|  
|E\/S|Trie les threads par le pourcentage du temps passé en E\/S \(lecture et écriture de données\).|  
|Sleep|Trie les threads par le pourcentage du temps passé en veille.|  
|Pagination|Trie les threads par le pourcentage du temps passé en pagination.|  
|Préemption|Trie les threads par le pourcentage du temps passé en préemption.|  
|Traitement IU|Trie les threads par le pourcentage du temps passé en traitement de l'interface utilisateur.|  
  
## Déplacer le canal sélectionné vers le haut ou le bas  
 Vous pouvez utiliser ces contrôles pour déplacer un canal en haut ou en bas dans la liste.  Par exemple, vous pouvez positionner les canaux connexes l'un à l'autre pour vous aider à tester un modèle particulier ou une relation interthreads.  
  
## Déplacer le canal sélectionné vers le début ou la fin  
 Vous pouvez déplacer les canaux sélectionnés en haut ou en bas de la liste afin que vous puissiez examiner un modèle particulier, ou déplacez des canaux à l'écart lorsque vous en examinez d'autres.  
  
## Canaux sélectionnés masqués  
 Sélectionnez le contrôle lorsque vous souhaitez masquer des canaux.  Par exemple, si un thread est à 100 % synchronisé pendant toute la durée du processus managé, vous pouvez le masquer pendant que vous analysez d'autres threads.  
  
> [!NOTE]
>  Lorsque vous masquez un thread, vous le supprimez également du calcul des durées, qui sont indiqués dans la légende active et dans les rapports de profil.  
  
## Afficher tous les canaux  
 Ce contrôle est actif lorsqu'un ou plusieurs canaux sont masqués.  Si vous les sélectionnez, tous les éléments masqués sont affichés et sont retournés des calculs du temps.  
  
## Déplacez les jetons vers le haut  
 Si une trace contient des événements de jeton, vous pouvez utiliser cette commande pour déplacer les canaux de jeton en haut de la chronologie.  Leur commande relative est conservée.  
  
## Groupe de jetons par processus  
 Si une trace contient des événements de jeton, vous pouvez utiliser cette commande pour regrouper des canaux de jeton dans le thread qui a généré les événements de jeton.  Les canaux de disque sont déplacés vers le haut de la liste des canaux et des canaux de GPU sont déplacés vers le bas.  
  
## Voir aussi  
 [Contrôle Zoom \(vue Threads\)](../profiling/zoom-control-threads-view.md)   
 [Mode Mesure activé\/désactivé](../profiling/measure-mode-on-off.md)   
 [vue Threads](../profiling/threads-view-parallel-performance.md)