---
title: Onglet Général, boîte de dialogue Propriétés de Thread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e8604c2d31f6bb50e9e77efbf6423f56ed719c0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714814"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Onglet Général de la boîte de dialogue Propriétés du thread
Utilisez cette boîte de dialogue pour en savoir plus sur un thread spécifique. Pour afficher cette boîte de dialogue, déplacez le focus à un [vue Threads](../debugger/threads-view.md) fenêtre, ou ouvrez [vue Messages](../debugger/messages-view.md) et développez un message. Sélectionnez n’importe quel nœud de thread dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.

 Le **propriétés du Thread** boîte de dialogue contient un seul volet, le **général** onglet. Les paramètres suivants sont disponibles :

|Entrée|Description|
|-----------|-----------------|
|**Nom du module**|Nom du module.|
|**ID de thread**|ID unique de ce thread. Notez que les numéros d’ID de thread sont réutilisés ; ils identifient un thread uniquement pour la durée de vie de ce thread.|
|**ID du processus**|ID unique de ce processus. Numéros d’ID de processus sont réutilisés, donc ils identifient un processus uniquement pour la durée de vie du processus. Le type d’objet de processus est créé lorsqu’un programme est exécuté. Tous les threads dans un processus partagent le même espace d’adressage et ont accès aux mêmes données. Choisissez cette valeur pour afficher les propriétés de l’ID de processus.|
|**État du thread**|L’état actuel du thread. Un thread en cours d’exécution utilise un processeur ; un thread de secours est sur le point d’utiliser un. Un Thread prêt attend de pouvoir utiliser un processeur, car aucun n’est libre. Un thread en cours de Transition est en attente d’une ressource pour s’exécuter, comme l’attente de sa pile d’exécution soit paginée à partir du disque. Un thread en attente n’a pas besoin du processeur, car il est en attente pour une opération de périphérique ou d’une ressource se libèrent.|
|**Raison de l’attente**|Cela s’applique uniquement lorsque le thread est en état d’attente. Les paires d’événements sont utilisés pour communiquer avec les sous-systèmes protégés.|
|**Temps CPU**|Temps processeur total passé sur ce processus et ses threads. Égal à temps utilisateur + temps privilégié.|
|**Temps utilisateur**|Temps total passé par ce thread à exécuter du code en Mode utilisateur. Applications s’exécutent en Mode utilisateur, tout comme les sous-systèmes tels que le Gestionnaire de fenêtres et le moteur de graphiques.|
|**Temps privilégié**|Temps total passé par ce thread à exécuter du code en Mode privilégié. Lorsqu’un service de système de Windows est appelé, le service s’exécute souvent en Mode privilégié pour accéder aux données privées du système. Ces données sont protégées contre tout accès par les threads s’exécutant en Mode utilisateur. Les appels au système peuvent être explicites ou implicites, telles que lorsqu’une erreur de page ou une interruption se produit.|
|**Temps écoulé**|Le temps total écoulé (en secondes) ce thread a été exécuté.|
|**Priorité actuelle**|La priorité actuelle dynamique de ce thread. Les threads d’un processus peuvent augmenter et réduire leur propre priorité de base par rapport à la priorité de base du processus.|
|**Priorité de base**|La priorité de base actuelle de ce thread.|
|**Adresse de début**|Adresse virtuelle initiale pour ce thread.|
|**PC de l’utilisateur**|Le compteur de programme utilisateur pour le thread.|
|**Commutateurs de contexte**|Le nombre de commutateurs d’un thread à un autre. Commutateurs de thread peuvent se produire à l’intérieur d’un processus unique ou entre processus. Un commutateur de thread peut être dû à un seul thread demandant des informations ou par un thread en cours lorsqu’un thread de priorité plus élevée est prêt à exécuter.|