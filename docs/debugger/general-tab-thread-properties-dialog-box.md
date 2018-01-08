---
title: "Onglet Général, boîte de dialogue Propriétés de Thread | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d8d53c373c58e31f2a2719df8afa6dd0da9cd3c6
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2018
---
# <a name="general-tab-thread-properties-dialog-box"></a>Onglet Général de la boîte de dialogue Propriétés du thread
Utilisez cette boîte de dialogue pour en savoir plus sur un thread spécifique. Pour afficher cette boîte de dialogue, déplacez le focus vers un [vue Threads](../debugger/threads-view.md) fenêtre, ou ouvrez [vue Messages](../debugger/messages-view.md) et développez un message. Sélectionnez n’importe quel nœud de thread dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Le **propriétés du Thread** boîte de dialogue contient un seul volet, le **général** onglet. Les paramètres suivants sont disponibles :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Nom du module**|Nom du module.|  
|**ID de thread**|ID unique de ce thread. Notez que les numéros d’ID de thread sont réutilisés ; ils identifient un thread uniquement pour la durée de vie de ce thread.|  
|**ID du processus**|ID unique de ce processus. Les numéros d’ID de processus sont réutilisés ils identifient un processus uniquement pour la durée de vie de ce processus. Le type d’objet Process est créé lorsqu’un programme est exécuté. Tous les threads dans un processus partagent le même espace d’adressage et ont accès aux mêmes données. Choisissez cette valeur pour afficher les propriétés de l’ID de processus.|  
|**État du thread**|L’état actuel du thread. Un thread en cours d’exécution utilise un processeur ; un thread de secours est sur le point d’utiliser une. Un Thread prêt attend d’utiliser un processeur, car un n’est pas disponible. Un thread en Transition attend une ressource d’exécution, comme l’attente de la pile d’exécution du fichier d’échange à partir du disque. Un thread en attente n’a pas besoin du processeur, car elle est en attente pour une opération de périphérique ou une ressource devienne disponible.|  
|**Raison de l’attente**|Cela s’applique uniquement lorsque le thread est dans l’état d’attente. Les paires d’événements sont utilisés pour communiquer avec les sous-systèmes protégés.|  
|**Temps processeur**|Temps processeur total passé sur ce processus et ses threads. Égal à temps utilisateur + temps privilégié.|  
|**Temps utilisateur**|Temps total passé par ce thread à exécuter du code en Mode utilisateur. Applications s’exécutent en Mode utilisateur, comme les sous-systèmes, tels que le Gestionnaire de fenêtrage et le moteur graphique.|  
|**Temps privilégié**|Temps total passé par ce thread à exécuter du code en Mode privilégié. Lorsqu’un service système Windows est appelé, le service s’exécute souvent en Mode privilégié pour accéder aux données privées du système. Ces données sont protégées contre tout accès threads s’exécutant en Mode utilisateur. Les appels système peuvent être explicites ou implicites, par exemple lorsqu’une erreur de page ou une interruption se produit.|  
|**Temps écoulé**|Le temps total écoulé (en secondes) ce thread a été exécuté.|  
|**Priorité actuelle**|La priorité actuelle dynamique de ce thread. Threads dans un processus peuvent augmenter et réduire leur propre priorité de base par rapport à la priorité de base du processus.|  
|**Priorité de base**|La priorité de base actuelle de ce thread.|  
|**Adresse de début**|Adresse de début virtuelle pour ce thread.|  
|**Utilisateur PC**|Le compteur de programme utilisateur du thread.|  
|**Changements de contexte**|Le nombre de commutateurs d’un thread à un autre. Commutateurs de thread peuvent se produire à l’intérieur d’un processus unique ou entre processus. Une commutation de threads peut être dû à un seul thread demandant des informations, ou par un thread qui est interrompu lorsqu’un thread de priorité supérieure est prêt à s’exécuter.|