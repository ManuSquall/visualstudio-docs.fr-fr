---
title: "Onglet Fichier d&#39;&#233;change de la bo&#238;te de dialogue Propri&#233;t&#233;s du processus | Microsoft Docs"
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
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Onglet Fichier d&#39;&#233;change de la bo&#238;te de dialogue Propri&#233;t&#233;s du processus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez l'onglet **Fichier d'échange** pour examiner le fichier de pagination d'un processus.  Pour afficher la [boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacez le focus sur une fenêtre [Vue Processus](../debugger/processes-view.md).  Sélectionnez n'importe quel nœud de processus dans l'arborescence, puis sélectionnez **Propriétés** dans le menu **Affichage**.  
  
 Les paramètres suivants sont disponibles sous l'onglet **Fichier d'échange** :  
  
|Entry|Description|  
|-----------|-----------------|  
|**Octets de fichier d'échange**|Nombre actuel de pages que ce processus utilise dans le fichier de pagination.  Le fichier de pagination stocke les pages de données utilisées par le processus mais non contenues dans d'autres fichiers.  Le fichier de pagination est utilisé par tous les processus ; par ailleurs, le manque d'espace dans le fichier de pagination peut provoquer des erreurs pendant l'exécution d'autres processus.|  
|**Nombre d'octets de fichier d'échange max.**|Nombre maximal de pages que ce processus a utilisées dans le fichier de pagination.|  
|**Erreurs de page**|Nombre d'erreurs de page des threads qui s'exécutent dans ce processus.  Une erreur de page se produit lorsqu'un thread fait référence à une page de mémoire virtuelle qui n'est pas dans son jeu de travail en mémoire principale.  Par conséquent, la page n'est pas récupérée à partir du disque si elle est en liste d'attente et déjà en mémoire principale, ou si elle est utilisée par un autre processus avec lequel la page est partagée.|