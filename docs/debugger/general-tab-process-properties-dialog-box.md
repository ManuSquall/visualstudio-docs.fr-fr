---
title: Onglet général de la boîte de dialogue Propriétés du processus | Microsoft Docs
description: Affichez l’onglet général pour obtenir des informations sur un processus, y compris le nom du module, l’ID de processus, la priorité de base, le nombre de threads, le temps processeur, l’heure utilisateur et le temps écoulé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dae82479044df6c031e5aa9f023b17c5e7902965
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870556"
---
# <a name="general-tab-process-properties-dialog-box"></a>Onglet Général de la boîte de dialogue Propriétés du processus
Utilisez l’onglet **général** pour en savoir plus sur un processus spécifique. Pour afficher la [boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacez le focus vers une fenêtre [vue processus](../debugger/processes-view.md) . Sélectionnez un nœud de processus dans l’arborescence, puis choisissez **Propriétés** dans le menu **affichage** .

 Les paramètres suivants sont disponibles sous l’onglet **général** :

|Entrée|Description|
|-----------|-----------------|
|**Nom du module**|Nom du module.|
|**ID de processus**|ID unique de ce processus. Les numéros d’identification de processus sont réutilisés, donc ils identifient un processus uniquement pendant la durée de vie de ce processus. Le type d’objet processus est créé lors de l’exécution d’un programme. Tous les threads d’un processus partagent le même espace d’adressage et ont accès aux mêmes données.|
|**Priorité de base**|Priorité de base actuelle de ce processus. Les threads d’un processus peuvent augmenter et diminuer leur propre priorité de base par rapport à la priorité de base du processus.|
|**Threads**|Nombre de threads actuellement actifs dans ce processus.|
|**Temps processeur**|Temps processeur total consacré à ce processus et à ses threads. Égal à heure de l’utilisateur plus temps privilégié.|
|**Temps utilisateur**|Temps écoulé cumulé que les threads de ce processus ont passé à exécuter du code en mode utilisateur dans des threads actifs. Les applications s’exécutent en mode utilisateur, tout comme les sous-systèmes tels que le gestionnaire de fenêtres et le moteur graphique.|
|**Temps privilégié**|Temps total écoulé que ce processus a été exécuté en mode privilégié dans les threads non inactifs. La couche de service, les routines Executive et le noyau s’exécutent en mode privilégié. Les pilotes de périphérique pour la plupart des appareils autres que les cartes graphiques et les imprimantes s’exécutent également en mode privilégié. Certaines tâches que Windows effectue pour votre application peuvent apparaître dans d’autres processus de sous-système en plus du temps privilégié.|
|**Temps écoulé**|Temps total écoulé pendant l’exécution de ce processus.|