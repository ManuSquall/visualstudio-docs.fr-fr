---
title: "Onglet G&#233;n&#233;ral de la bo&#238;te de dialogue Propri&#233;t&#233;s du processus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propriétés du processus pour Windows NT"
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Onglet G&#233;n&#233;ral de la bo&#238;te de dialogue Propri&#233;t&#233;s du processus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez l'onglet **Général** pour obtenir des informations supplémentaires sur un processus spécifique.  Pour afficher la [boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacez le focus sur une fenêtre [Vue Processus](../debugger/processes-view.md).  Sélectionnez n'importe quel nœud de processus dans l'arborescence, puis sélectionnez **Propriétés** dans le menu **Affichage**.  
  
 Les paramètres suivants sont disponibles sous l'onglet **Général** :  
  
|Entry|Description|  
|-----------|-----------------|  
|**Nom de module**|Nom du module.|  
|**ID de processus**|ID unique de ce processus.  Les numéros d'ID de processus sont réutilisés. Ainsi, ils identifient un processus uniquement pour la durée de vie de ce processus.  Le type d'objet Process est créé lorsqu'un programme est exécuté.  Tous les threads d'un processus partagent le même espace d'adressage et ont accès aux mêmes données.|  
|**Priorité de base**|Priorité de base actuelle de ce processus.  Les threads d'un processus peuvent élever et abaisser leur propre priorité de base par rapport à la priorité de base du processus.|  
|**Threads**|Nombre de threads actifs dans ce processus.|  
|**Temps CPU**|Temps processeur total consacré à ce processus et à ses threads.  Équivaut à Temps utilisateur \+ Temps privilégié.|  
|**Temps utilisateur**|Temps cumulé consacré par les threads de ce processus à l'exécution du code en mode utilisateur dans des threads non inactifs.  Les applications s'exécutent en mode utilisateur, à l'instar des sous\-systèmes comme le Gestionnaire de fenêtrage et le moteur graphique.|  
|**Temps privilégié**|Durée totale \(en secondes\) d'exécution de ce processus en mode privilégié dans des threads non inactifs.  La couche Service, les routines exécutives et le noyau s'exécutent en mode privilégié.  Les pilotes de la plupart des périphériques autres que les cartes graphiques et les imprimantes s'exécutent également en mode privilégié.  Certaines tâches exécutées par Windows pour votre application peuvent apparaître dans d'autres processus sous\-système en plus du temps privilégié.|  
|**Temps écoulé**|Durée totale d'exécution de ce processus.|