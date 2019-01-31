---
title: Onglet Général de traiter la boîte de dialogue Propriétés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41667abc250bc2b2ffc869b714fafbcae8f21297
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931958"
---
# <a name="general-tab-process-properties-dialog-box"></a>Onglet Général de la boîte de dialogue Propriétés du processus
Utilisez le **général** onglet pour en savoir plus sur un processus spécifique. Pour afficher le [boîte de dialogue Propriétés de processus](../debugger/process-properties-dialog-box.md), déplacez le focus à un [vue processus](../debugger/processes-view.md) fenêtre. Sélectionnez n’importe quel nœud de processus dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **général** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Nom du module**|Nom du module.|  
|**ID du processus**|ID unique de ce processus. Numéros d’ID de processus sont réutilisés, donc ils identifient un processus uniquement pour la durée de vie du processus. Le type d’objet de processus est créé lorsqu’un programme est exécuté. Tous les threads dans un processus partagent le même espace d’adressage et ont accès aux mêmes données.|  
|**Priorité de base**|La priorité de base en cours de ce processus. Les threads d’un processus peuvent augmenter et réduire leur propre priorité de base par rapport à la priorité de base du processus.|  
|**Threads**|Le nombre de threads actuellement actifs dans ce processus.|  
|**Temps processeur**|Temps processeur total passé sur ce processus et ses threads. Égal à temps utilisateur plus temps privilégié.|  
|**Temps utilisateur**|Le temps total que les threads de ce processus ont passé à exécuter du code en Mode utilisateur dans des threads actifs. Applications s’exécutent en Mode utilisateur, tout comme les sous-systèmes tels que le Gestionnaire de fenêtres et le moteur de graphiques.|  
|**Temps privilégié**|Le temps total écoulé ce processus a été exécuté en Mode privilégié dans des threads actifs. La couche de service, les routines Executive et le noyau s’exécutent en Mode privilégié. Pilotes de périphérique pour la plupart des périphériques autres que les cartes graphiques et des imprimantes s’exécutent également en Mode privilégié. Certains travaux par Windows pour votre application peut-être apparaître dans d’autres processus de sous-système en plus de temps privilégié.|  
|**Temps écoulé**|Le temps total écoulé que ce processus a été exécuté.|