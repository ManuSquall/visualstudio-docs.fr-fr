---
title: Onglet de la mémoire, de la boîte de dialogue Propriétés de processus | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 724e760c585f0e6423164e1a6bb28aefbf696c2f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245795"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Onglet Mémoire de la boîte de dialogue Propriétés du processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilisez le **mémoire** tab pour montrer comment un processus utilise la mémoire. Pour afficher le [boîte de dialogue Propriétés de processus](../debugger/process-properties-dialog-box.md), déplacez le focus à un [vue processus](../debugger/processes-view.md) fenêtre. Sélectionnez n’importe quel nœud de processus dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **mémoire** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Octets virtuels**|La taille actuelle (en octets) de l’espace d’adressage virtuel que le processus utilise. L’utilisation de l’espace d’adressage virtuel n’implique pas nécessairement une utilisation correspondante du disque ou des pages de mémoire principales. Toutefois, l’espace virtuel reste limité, et à l’aide de trop peut-être limiter la capacité du processus à charger des bibliothèques.|  
|**Octets virtuels maximal**|Le nombre maximal d’octets d’espace d’adressage virtuel du processus a utilisé à tout moment.|  
|**Plage de travail**|Le jeu de pages mémoire touchées récemment par les threads dans le processus. Si la mémoire disponible de l’ordinateur est au-dessus d’un seuil, les pages sont laissées dans la plage de travail d’un processus même si elles ne sont pas en cours d’utilisation. Lors de la mémoire disponible tombe en dessous d’un seuil, les pages sont retirées de la plage de travail. S’ils sont nécessaires, elles seront de ramenées dans la plage de travail avant de quitter la mémoire principale.|  
|**Plage de travail maximale**|Le nombre maximal de pages dans la plage de travail de ce processus à un moment donné.|  
|**Octets de réserve paginée**|La quantité actuelle de réserve paginée, que le processus a allouée. Réserve paginée est une zone de mémoire système où les composants de système d’exploitation acquièrent de l’espace comme ils accomplissement leurs tâches désignés. Pages de réserve paginée peuvent être transférées vers le fichier d’échange ne pas accessibles par le système pour des périodes prolongées.|  
|**Octets de réserve non paginée**|Le nombre actuel d’octets dans la réserve non paginée allouée par le processus. La réserve non paginée est une zone de mémoire système où l’espace est acquis par les composants du système d’exploitation comme ils accomplissement leurs tâches désignés. Pages de réserve non paginée ne peut pas être transférées vers le fichier d’échange ; ils restent dans la mémoire principale tant qu’ils sont alloués.|  
|**Octets privés**|Le nombre actuel d’octets que ce processus a alloué qui ne peut pas être partagé avec d’autres processus.|  
|**Octets libres**|L’espace d’adressage virtuel inutilisé de ce processus.|  
|**Octets réservés**|La quantité totale de mémoire virtuelle réservée pour une utilisation ultérieure par ce processus.|  
|**Octets d’Image libres**|La quantité d’espace d’adressage virtuel qui n’est pas en cours d’utilisation ou réservée par les images au sein de ce processus.|  
|**Octets d’Image réservés**|La somme de toute la mémoire virtuelle réservée par les images exécutées au sein de ce processus.|



