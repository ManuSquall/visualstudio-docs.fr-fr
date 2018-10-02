---
title: Onglet espace, boîte de dialogue Propriétés de processus | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78f65edeec910bd0667bfc369ff1d4cbddb54813
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502652"
---
# <a name="space-tab-process-properties-dialog-box"></a>Onglet Espace de la boîte de dialogue Propriétés du processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [onglet espace, la boîte de dialogue Propriétés du processus](https://docs.microsoft.com/visualstudio/debugger/space-tab-process-properties-dialog-box).  
  
Utilisez le **espace** onglet pour examiner l’espace d’adressage d’un processus. Pour afficher le [boîte de dialogue Propriétés de processus](../debugger/process-properties-dialog-box.md), déplacez le focus à un [vue processus](../debugger/processes-view.md) fenêtre. Sélectionnez n’importe quel nœud de processus dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **espace** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Afficher l’espace marqué comme**|Utilisez cette zone de liste pour sélectionner la catégorie d’espace (image, mappé, réservé ou non assigné).|  
|**Octets exécutables**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage à l’aide de ce processus. La mémoire exécutable est la mémoire qui peut être exécutée par des programmes, mais qui ne peut pas être lues ou écrite.|  
|**Octets EXEC-lecture seule**|Pour la catégorie sélectionnée, la somme de l’espace d’adressage en cours d’utilisation avec des propriétés en lecture seule à l’aide de ce processus. Mémoire EXEC-read-only est qui peut être exécutée tant la lecture.|  
|**Octets EXEC-lecture-écriture**|Pour la catégorie sélectionnée, la somme de l’espace d’adressage en cours d’utilisation avec des propriétés en lecture-écriture à l’aide de ce processus. Mémoire EXEC-lecture-écriture est la mémoire qui peut être exécutée par des programmes ainsi que lire et modifié.|  
|**Octets d’écriture de EXEC de copie**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage qui peut être exécutée par des programmes ainsi que lue et modifiée. Ce type de protection est utilisé lors de la mémoire doit être partagé entre les processus. Si les processus de partage uniquement lire la mémoire, puis ils utiliseront tous la même mémoire. Si un processus de partage désire un accès en écriture, puis une copie de cette mémoire sera pour le processus.|  
|**Octets sans accès**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage qui empêche un processus de l’utiliser. Une violation d’accès est générée si l’écriture ou lecture est tentée.|  
|**Octets en lecture seule**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage qui peut être exécuté ainsi que lire.|  
|**Octets lecture-écriture**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage qui permet de lire et écrire.|  
|**Octets écriture-copie**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage qui autorise le partage de mémoire pour la lecture mais pas pour l’écriture. Lorsque des processus lisent cette mémoire, ils peuvent partager la même mémoire. Toutefois, lorsqu’un processus de partage souhaite avoir accès en lecture/écriture à cette mémoire partagée, une copie de cette mémoire est effectuée pour l’écriture.|



