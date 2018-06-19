---
title: Onglet de la mémoire, la boîte de dialogue Propriétés du processus | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b43dd047e4ebdb145092dc3b9f37098b8db6322e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474617"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Onglet Mémoire de la boîte de dialogue Propriétés du processus
Utilisez le **mémoire** tab pour montrer comment un processus utilise la mémoire. Pour afficher le [la boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacer le focus à un [vue processus](../debugger/processes-view.md) fenêtre. Sélectionnez n’importe quel nœud de processus dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **mémoire** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Octets virtuels**|La taille actuelle (en octets) de l’espace d’adressage virtuel que le processus utilise. L’utilisation de l’espace d’adressage virtuel n’implique pas nécessairement une utilisation correspondante du disque ou des pages de mémoire principales. Toutefois, l’espace virtuel est fini, et à l’aide de trop peut limiter la capacité du processus à charger des bibliothèques.|  
|**Octets virtuels maximal**|Le nombre maximal d’octets d’espace d’adressage virtuel du processus a utilisé à tout moment.|  
|**Plage de travail**|Le jeu de pages mémoire touchées récemment par les threads dans le processus. Si la mémoire disponible de l’ordinateur est au-dessus d’un seuil, les pages sont laissées dans la plage de travail d’un processus même si elles ne sont pas en cours d’utilisation. Lors de la mémoire disponible tombe en dessous d’un seuil, les pages sont retirées du jeu de travail. S’ils sont nécessaires, elles seront de ramenées dans la plage de travail avant de quitter la mémoire principale.|  
|**Plage de travail maximale**|Le nombre maximal de pages dans le jeu de travail de ce processus à un moment donné.|  
|**Octets de réserve paginée**|Quantité actuelle de réserve paginée le processus a allouée. Réserve paginée est une zone de mémoire système où les composants de système d’exploitation acquièrent de l’espace que leurs tâches désigné. Pages de réserve paginée peuvent être transférées vers le fichier d’échange lorsque ne pas accédé par le système pour des périodes prolongées.|  
|**Octets de réserve non paginée**|Le nombre actuel d’octets dans la réserve non paginée allouée par le processus. La réserve non paginée est une zone de mémoire système où l’espace est acquis par les composants du système d’exploitation que leurs tâches désigné. Pages de réserve non paginée ne peuvent pas être transférées vers le fichier d’échange ; ils restent dans la mémoire principale tant qu’ils sont alloués.|  
|**Octets privés**|Le nombre actuel d’octets que ce processus a alloué et qui ne peut pas être partagé avec d’autres processus.|  
|**Octets libres**|L’espace d’adressage virtuel inutilisé de ce processus.|  
|**Octets réservés**|La quantité totale de mémoire virtuelle réservée pour une utilisation ultérieure par ce processus.|  
|**Octets d’Image libres**|La quantité d’espace d’adressage virtuel qui n’est pas en cours d’utilisation ou réservée par des images dans ce processus.|  
|**Octets d’Image réservés**|La somme de la mémoire virtuelle réservée par les images exécutées par ce processus.|