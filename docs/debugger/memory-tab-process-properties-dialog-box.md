---
title: Onglet mémoire de la boîte de dialogue Propriétés du processus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bdfc2740094c807818922f09ca3fef0a21c9e1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62931280"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Onglet Mémoire de la boîte de dialogue Propriétés du processus
Utilisez l’onglet **mémoire** pour afficher la façon dont un processus utilise la mémoire. Pour afficher la [boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacez le focus vers une fenêtre [vue processus](../debugger/processes-view.md) . Sélectionnez un nœud de processus dans l’arborescence, puis choisissez **Propriétés** dans le menu **affichage** .

 Les paramètres suivants sont disponibles sous l’onglet **mémoire** :

|Entrée|Description|
|-----------|-----------------|
|**Octets virtuels**|Taille actuelle (en octets) de l’espace d’adressage virtuel utilisé par le processus. L’utilisation de l’espace d’adressage virtuel n’implique pas nécessairement l’utilisation correspondante du disque ou des pages de mémoire principales. Toutefois, l’espace virtuel est limité et l’utilisation trop importante peut limiter la capacité du processus à charger des bibliothèques.|
|**Nombre d’octets virtuels maximal**|Nombre maximal d’octets d’espace d’adressage virtuel que le processus a utilisés à un moment donné.|
|**Plage de travail**|Ensemble de pages mémoire touchées récemment par les threads du processus. Si la mémoire disponible de l'ordinateur dépasse un certain seuil, les pages sont laissées dans la Plage de travail d'un processus même si elles ne sont pas utilisées. Lorsque la mémoire disponible tombe en dessous d’un seuil, les pages sont supprimées de la plage de travail. Si elles sont nécessaires, elles seront ramenées après un défaut de service dans la plage de travail avant qu’elles ne laissent la mémoire centrale.|
|**Nombre de jeux de travail maximal**|Nombre maximal de pages dans la plage de travail de ce processus à un moment donné.|
|**Octets regroupés paginés**|Quantité actuelle de réserve paginée allouée par le processus. La réserve paginée est une zone de mémoire système dans laquelle les composants du système d’exploitation acquièrent de l’espace lorsqu’ils accomplissent leurs tâches nommées. Les pages de réserve paginée peuvent être paginées dans le fichier de pagination lorsqu’elles ne sont pas accessibles par le système pendant des périodes prolongées.|
|**Octets regroupés non paginés**|Nombre actuel d’octets dans la réserve non paginée allouée par le processus. La réserve non paginée est une zone de mémoire système dans laquelle l’espace est acquis par les composants du système d’exploitation lors de l’exécution de leurs tâches nommées. Les pages de réserve non paginée ne peuvent pas être paginées dans le fichier d’échange ; ils restent dans la mémoire principale tant qu’ils sont alloués.|
|**Octets privés**|Nombre actuel d’octets alloués par ce processus et qui ne peuvent pas être partagés avec d’autres processus.|
|**Octets libres**|Espace d’adressage virtuel inutilisé total de ce processus.|
|**Octets réservés**|Quantité totale de mémoire virtuelle réservée pour une utilisation future par ce processus.|
|**Octets d’image libres**|Quantité d’espace d’adressage virtuel qui n’est pas utilisée ou réservée par les images au cours de ce processus.|
|**Octets d’image réservés**|Somme de toute la mémoire virtuelle réservée par les images exécutées dans ce processus.|