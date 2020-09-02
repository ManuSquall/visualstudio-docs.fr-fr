---
title: Onglet général de la boîte de dialogue Propriétés du thread | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62896365"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Onglet Général de la boîte de dialogue Propriétés du thread
Utilisez cette boîte de dialogue pour en savoir plus sur un thread spécifique. Pour afficher cette boîte de dialogue, déplacez le focus vers une fenêtre [vue threads](../debugger/threads-view.md) , ou ouvrez la [vue messages](../debugger/messages-view.md) et développez un message. Sélectionnez n’importe quel nœud de thread dans l’arborescence, puis choisissez **Propriétés** dans le menu **affichage** .

 La boîte de dialogue **Propriétés du thread** contient un volet, l’onglet **général** . Les paramètres suivants sont disponibles :

|Entrée|Description|
|-----------|-----------------|
|**Nom du module**|Nom du module.|
|**ID du thread**|ID unique de ce thread. Notez que les numéros d’ID de thread sont réutilisés ; ils identifient un thread uniquement pendant la durée de vie de ce thread.|
|**ID de processus**|ID unique de ce processus. Les numéros d’identification de processus sont réutilisés, donc ils identifient un processus uniquement pendant la durée de vie de ce processus. Le type d’objet processus est créé lors de l’exécution d’un programme. Tous les threads d’un processus partagent le même espace d’adressage et ont accès aux mêmes données. Choisissez cette valeur pour afficher les propriétés de l’ID de processus.|
|**État du thread**|État actuel du thread. Un thread en cours d’exécution utilise un processeur ; un thread de secours est sur le paragraphe d’en utiliser un. Un thread prêt attend d’utiliser un processeur, car aucun n’est disponible. Un thread en transition attend une ressource pour s’exécuter, par exemple en attendant que sa pile d’exécution soit paginée à partir du disque. Un thread en attente n’a pas besoin du processeur, car il attend qu’une opération de périphérique se termine ou qu’une ressource soit libérée.|
|**Raison de l’attente**|Cela s’applique uniquement lorsque le thread est en état d’attente. Les paires d’événements sont utilisées pour communiquer avec des sous-systèmes protégés.|
|**Temps processeur**|Temps processeur total consacré à ce processus et à ses threads. Égal à heure de l’utilisateur + temps privilégié.|
|**Temps utilisateur**|Temps écoulé total passé par ce thread à exécuter du code en mode utilisateur. Les applications s’exécutent en mode utilisateur, à l’instar des sous-systèmes tels que le gestionnaire de fenêtres et le moteur graphique.|
|**Temps privilégié**|Temps écoulé total passé par ce thread à exécuter du code en mode privilégié. Lorsqu’un service système Windows est appelé, le service s’exécute souvent en mode privilégié pour accéder aux données privées du système. Ces données sont protégées de l’accès par les threads qui s’exécutent en mode utilisateur. Les appels au système peuvent être explicites, ou ils peuvent être implicites, par exemple lorsqu’une erreur de page ou une interruption se produit.|
|**Temps écoulé**|Temps total écoulé (en secondes) d’exécution de ce thread.|
|**Priorité actuelle**|Priorité dynamique actuelle de ce thread. Les threads d’un processus peuvent augmenter et diminuer leur propre priorité de base par rapport à la priorité de base du processus.|
|**Priorité de base**|Priorité de base actuelle de ce thread.|
|**Adresse de début**|Adresse virtuelle de départ pour ce thread.|
|**PC de l’utilisateur**|Compteur de programme utilisateur pour le thread.|
|**Commutateurs de contexte**|Nombre de commutateurs d’un thread à un autre. Les commutateurs de thread peuvent se trouver à l’intérieur d’un processus unique ou d’un processus à l’autre. Un basculement de thread peut être provoqué par un thread qui demande des informations à un autre, ou par un thread en cours de préemption lorsqu’un thread de priorité plus élevée est prêt à être exécuté.|