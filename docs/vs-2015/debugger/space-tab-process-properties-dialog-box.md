---
title: Onglet espace de la boîte de dialogue Propriétés du processus | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: de5df4c55feba8c9aaba0def7585029cc71426b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189426"
---
# <a name="space-tab-process-properties-dialog-box"></a>Onglet Espace de la boîte de dialogue Propriétés du processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilisez l’onglet **espace** pour examiner l’espace d’adressage d’un processus. Pour afficher la [boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacez le focus vers une fenêtre [vue processus](../debugger/processes-view.md) . Sélectionnez un nœud de processus dans l’arborescence, puis choisissez **Propriétés** dans le menu **affichage** .  
  
 Les paramètres suivants sont disponibles sous l’onglet **espace** :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Afficher l’espace marqué comme**|Utilisez cette zone de liste pour sélectionner la catégorie d’espace (image, mappée, réservée ou non assignée).|  
|**Octets exécutables**|Pour la catégorie sélectionnée, somme de l’ensemble de l’espace d’adressage que ce processus utilise. La mémoire exécutable est une mémoire qui peut être exécutée par des programmes, mais qui n’est pas accessible en lecture ou en écriture.|  
|**Octets exécutables-lecture seule**|Pour la catégorie sélectionnée, somme de l’ensemble de l’espace d’adressage utilisé avec les propriétés en lecture seule que ce processus utilise. La mémoire d’exécution en lecture seule est une mémoire qui peut être exécutée et lue.|  
|**Octets exécutables-lecture-écriture**|Pour la catégorie sélectionnée, somme de l’ensemble de l’espace d’adressage utilisé avec les propriétés de lecture-écriture utilisées par ce processus. La mémoire exec-Read-Write est une mémoire qui peut être exécutée par les programmes et être lue et modifiée.|  
|**Octets de copie exec-Write**|Pour la catégorie sélectionnée, somme de tous les espaces d’adressage qui peuvent être exécutés par les programmes, ainsi que de la lecture et de l’écriture. Ce type de protection est utilisé lorsque la mémoire doit être partagée entre les processus. Si les processus de partage ne lisent que la mémoire, ils utilisent tous la même mémoire. Si un processus de partage souhaite un accès en écriture, une copie de cette mémoire est effectuée pour le processus.|  
|**Octets sans accès**|Pour la catégorie sélectionnée, somme de tout l’espace d’adressage qui empêche un processus de l’utiliser. Une violation d’accès est générée en cas de tentative d’écriture ou de lecture.|  
|**Octets lecture seule**|Pour la catégorie sélectionnée, somme de tous les espaces d’adressage qui peuvent être exécutés et lus.|  
|**Octets lecture-écriture**|Pour la catégorie sélectionnée, somme de l’ensemble de l’espace d’adressage qui autorise la lecture et l’écriture.|  
|**Octets écriture-copie**|Pour la catégorie sélectionnée, somme de tout l’espace d’adressage qui autorise le partage de mémoire pour la lecture, mais pas pour l’écriture. Lorsque des processus lisent cette mémoire, ils peuvent partager la même mémoire. Toutefois, lorsqu’un processus de partage souhaite disposer d’un accès en lecture/écriture à cette mémoire partagée, une copie de cette mémoire est créée pour l’écriture.|
