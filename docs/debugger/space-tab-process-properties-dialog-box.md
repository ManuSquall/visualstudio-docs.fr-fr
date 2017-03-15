---
title: "Onglet Espace de la bo&#238;te de dialogue Propri&#233;t&#233;s du processus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propriétés du processus pour Windows NT"
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Onglet Espace de la bo&#238;te de dialogue Propri&#233;t&#233;s du processus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez l'onglet **Espace** pour examiner l'espace d'adressage d'un processus.  Pour afficher la [boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacez le focus sur une fenêtre [Vue Processus](../debugger/processes-view.md).  Sélectionnez n'importe quel nœud de processus dans l'arborescence, puis sélectionnez **Propriétés** dans le menu **Affichage**.  
  
 Les paramètres suivants sont disponibles sous l'onglet **Espace** :  
  
|Entry|Description|  
|-----------|-----------------|  
|**Afficher l'espace marqué comme**|Utilisez cette zone de liste pour sélectionner la catégorie de l'espace \(image, mappé, réservé ou non assigné\).|  
|**Octets exécutables**|Pour la catégorie sélectionnée, somme de l'ensemble de l'espace d'adressage utilisé par ce processus.  La mémoire exécutable est la mémoire qui peut être exécutée par les programmes, mais qui n'est pas accessible en lecture ou en écriture.|  
|**Octets exécutables\-lecture seule**|Pour la catégorie sélectionnée, somme de l'ensemble de l'espace d'adressage avec des propriétés en lecture seule que ce processus utilise.  Il s'agit de la mémoire qui peut être exécutée et être accessible en lecture.|  
|**Octets exécutables\-lecture\-écriture**|Pour la catégorie sélectionnée, somme de l'ensemble de l'espace d'adressage avec des propriétés en lecture\/écriture que ce processus utilise.  Il s'agit de la mémoire qui peut être exécutée par les programmes et être accessible en lecture\/écriture.|  
|**Octets exécutables\-écriture\-copie**|Pour la catégorie sélectionnée, somme de l'ensemble de l'espace d'adressage qui peut être exécuté par les programmes et être accessible en lecture\/écriture.  Ce type de protection est utilisé lorsque la mémoire doit être partagée entre des processus.  Si les processus de partage lisent seulement la mémoire, ils utiliseront tous la même mémoire.  Si un processus de partage désire l'accès en écriture, une copie de cette mémoire sera effectuée pour le processus.|  
|**Octets sans accès**|Pour la catégorie sélectionnée, somme de l'ensemble de l'espace d'adressage qui ne peut pas être utilisé par un processus.  Une violation d'accès est générée en cas de tentative d'écriture ou de lecture.|  
|**Octets lecture seule**|Pour la catégorie sélectionnée, somme de l'ensemble de l'espace d'adressage qui peut être exécuté et être accessible en lecture.|  
|**Octets lecture\-écriture**|Pour la catégorie sélectionnée, somme de l'ensemble de l'espace d'adressage qui autorise la lecture et l'écriture.|  
|**Octets écriture\-copie**|Pour la catégorie sélectionnée, somme de l'ensemble de l'espace d'adressage qui autorise le partage de la mémoire pour la lecture mais pas pour l'écriture.  Lorsque les processus lisent cette mémoire, ils peuvent partager la même mémoire.  Toutefois, lorsqu'un processus de partage souhaite disposer d'un accès en lecture\/écriture à cette mémoire partagée, une copie de cette mémoire est effectuée pour l'écriture.|