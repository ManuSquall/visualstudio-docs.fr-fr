---
title: Onglet Général de traiter la boîte de dialogue Propriétés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3dcefc8be643c74349102261725c4879c0e161cd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="general-tab-process-properties-dialog-box"></a>Onglet Général de la boîte de dialogue Propriétés du processus
Utilisez le **général** onglet pour en savoir plus sur un processus spécifique. Pour afficher le [la boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacer le focus à un [vue processus](../debugger/processes-view.md) fenêtre. Sélectionnez n’importe quel nœud de processus dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **général** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Nom du module**|Nom du module.|  
|**ID du processus**|ID unique de ce processus. Les numéros d’ID de processus sont réutilisés ils identifient un processus uniquement pour la durée de vie de ce processus. Le type d’objet Process est créé lorsqu’un programme est exécuté. Tous les threads dans un processus partagent le même espace d’adressage et ont accès aux mêmes données.|  
|**Priorité de Base**|La priorité de base actuelle de ce processus. Threads d’un processus peuvent augmenter et réduire leur propre priorité de base par rapport à la priorité de base du processus.|  
|**Threads**|Le nombre de threads actuellement actifs dans ce processus.|  
|**Temps processeur**|Temps processeur total passé sur ce processus et ses threads. Égal à temps utilisateur + temps privilégié.|  
|**Temps utilisateur**|Le temps total que les threads de ce processus ont passé à exécuter du code en Mode utilisateur dans des threads non inactifs. Applications s’exécutent en Mode utilisateur, tout comme les sous-systèmes tels que le Gestionnaire de fenêtrage et le moteur graphique.|  
|**Temps privilégié**|Le temps total écoulé ce processus a été démarré en Mode privilégié dans des threads non inactifs. La couche de service, les routines Executive et le noyau s’exécutent en Mode privilégié. Pilotes de périphérique pour la plupart des périphériques autres que les cartes graphiques et les imprimantes s’exécutent également en Mode privilégié. Certaines tâches exécutées par Windows pour votre application peuvent apparaître dans d’autres processus de sous-système en plus du temps privilégié.|  
|**Temps écoulé**|Le temps total écoulé que ce processus a été exécuté.|