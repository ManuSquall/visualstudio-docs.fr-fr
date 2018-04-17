---
title: Onglet espace, la boîte de dialogue Propriétés du processus | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81d5329a694ba032a4dda280cac3a3200081aa77
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="space-tab-process-properties-dialog-box"></a>Onglet Espace de la boîte de dialogue Propriétés du processus
Utilisez le **espace** onglet pour examiner l’espace d’adressage d’un processus. Pour afficher le [la boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacer le focus à un [vue processus](../debugger/processes-view.md) fenêtre. Sélectionnez n’importe quel nœud de processus dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **espace** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Afficher l’espace marqué comme**|Utilisez cette zone de liste pour sélectionner la catégorie d’espace (image, mappé, réservé ou non assigné).|  
|**Octets exécutables**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage à l’aide de ce processus. La mémoire exécutable est la mémoire qui peut être exécutée par les programmes, mais qui ne peut-être pas être lues ou écrite.|  
|**Octets EXEC-lecture seule**|Pour la catégorie sélectionnée, la somme de l’espace d’adressage utilisé avec des propriétés en lecture seule à l’aide de ce processus. Mémoire EXEC-lecture seule est qui peut être exécutée tant la lecture.|  
|**Octets de lecture / écriture EXEC**|Pour la catégorie sélectionnée, la somme de l’espace d’adressage en cours d’utilisation avec des propriétés en lecture-écriture à l’aide de ce processus. EXEC-lecture-écriture est la mémoire qui peut être exécutée par des programmes ainsi que lire et modifié.|  
|**Octets d’écriture-EXEC de copie**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage qui peut être exécutée par des programmes ainsi que lue et modifiée. Ce type de protection est utilisé lors de la mémoire doit être partagé entre les processus. Si les processus de partage que lire la mémoire, puis ils utiliseront tous la même mémoire. Si un processus de partage désire un accès en écriture, puis une copie de cette mémoire sera pour le processus.|  
|**Octets sans accès**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage qui empêche un processus de l’utiliser. Une violation d’accès est générée si l’écriture ou de la tentative de lecture.|  
|**Octets en lecture seule**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage qui peut être exécutée tant la lecture.|  
|**Octets de lecture-écriture.**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage qui permet la lecture et en écriture.|  
|**Octets de la copie de l’écriture**|Pour la catégorie sélectionnée, la somme de tout l’espace d’adressage qui autorise le partage de mémoire pour la lecture mais pas pour l’écriture. Lorsque des processus lisent cette mémoire, ils peuvent partager la même mémoire. Toutefois, lorsqu’un processus veut avoir accès en lecture/écriture à cette mémoire partagée, une copie de cette mémoire est effectuée pour l’écriture.|