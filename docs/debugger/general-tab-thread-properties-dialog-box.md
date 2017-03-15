---
title: "Onglet G&#233;n&#233;ral de la bo&#238;te de dialogue Propri&#233;t&#233;s du thread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threads (Visual Studio), propriétés de thread"
  - "propriétés de thread"
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Onglet G&#233;n&#233;ral de la bo&#238;te de dialogue Propri&#233;t&#233;s du thread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez cette boîte de dialogue pour en savoir plus sur un thread spécifique.  Pour afficher cette boîte de dialogue, déplacez le focus sur une fenêtre [Vue Threads](../debugger/threads-view.md) ou ouvrez [Vue Messages](../debugger/messages-view.md) et développez un message.  Sélectionnez n'importe quel nœud de thread dans l'arborescence, puis sélectionnez **Propriétés** dans le menu **Affichage**.  
  
 La boîte de dialogue **Propriétés du thread** contient un seul volet, l'onglet **Général**.  Les paramètres suivants sont disponibles :  
  
|Entry|Description|  
|-----------|-----------------|  
|**Nom de module**|Nom du module.|  
|**ID de thread**|ID unique de ce thread.  Notez que les numéros d'ID de thread sont réutilisés ; ils identifient un thread uniquement pour la durée de vie de ce thread.|  
|**ID de processus**|ID unique de ce processus.  Les numéros d'ID de processus sont réutilisés. Ainsi, ils identifient un processus uniquement pour la durée de vie de ce processus.  Le type d'objet Process est créé lorsqu'un programme est exécuté.  Tous les threads d'un processus partagent le même espace d'adressage et ont accès aux mêmes données.  Choisissez cette valeur pour afficher les propriétés de l'ID de processus.|  
|**État du thread**|État actuel du thread.  Un thread en cours d'exécution utilise un processeur ; un thread de secours va en utiliser un.  Un thread prêt attend de pouvoir utiliser un processeur, car il n'y en a aucun de libre.  Un thread en transition attend qu'une ressource s'exécute ; par exemple, il attend que sa pile d'exécution soit paginée à partir du disque.  Un thread en attente n'a pas besoin du processeur, car il attend la fin d'une opération de périphérique ou la libération d'une ressource.|  
|**Raison de l'attente**|S'applique uniquement lorsque le thread est à l'état d'attente.  Les paires d'événements sont utilisées pour communiquer avec les sous\-systèmes protégés.|  
|**Temps CPU**|Temps processeur total consacré à ce processus et à ses threads.  Équivaut à Temps utilisateur \+ Temps privilégié.|  
|**Temps utilisateur**|Temps total consacré par ce thread à l'exécution du code en mode utilisateur.  Les applications s'exécutent en mode utilisateur, à l'instar des sous\-systèmes comme le Gestionnaire de fenêtrage et le moteur graphique.|  
|**Temps privilégié**|Temps total consacré par ce thread à l'exécution du code en mode privilégié.  Lorsqu'un service système Windows est appelé, il s'exécute souvent en mode privilégié pour accéder aux données privées du système.  L'accès à ces données est protégé par les threads qui s'exécutent en mode utilisateur.  Les appels au système peuvent être explicites, ou implicites, par exemple lorsqu'un défaut de page ou une interruption se produit.|  
|**Temps écoulé**|Durée totale \(en secondes\) d'exécution du thread.|  
|**Priorité actuelle**|Priorité dynamique actuelle de ce thread.  Les threads d'un processus peuvent élever et abaisser leur propre priorité de base par rapport à la priorité de base du processus.|  
|**Priorité de base**|Priorité de base actuelle de ce thread.|  
|**Adresse de début**|Adresse virtuelle de début de ce thread.|  
|**User PC**|Compteur de programme utilisateur du thread.|  
|**Changements de contexte**|Nombre de basculements d'un thread à un autre.  Les basculements de threads peuvent se produire à l'intérieur d'un processus unique ou entre plusieurs processus.  Un basculement de thread peut être déclenché par un thread qui demande des informations à un autre thread, ou par un thread qui est interrompu lorsqu'un thread de priorité supérieure est prêt à s'exécuter.|