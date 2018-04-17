---
title: Onglet fichier d’échange, la boîte de dialogue Propriétés du processus | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c5a0b5b498eacab4f53471530f51f8c59aed25e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Onglet Fichier d'échange de la boîte de dialogue Propriétés du processus
Utilisez le **Page fichier** onglet pour examiner le fichier d’échange d’un processus. Pour afficher le [la boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacer le focus à un [vue processus](../debugger/processes-view.md) fenêtre. Sélectionnez n’importe quel nœud de processus dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **Page fichier** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Octets de fichier d’échange**|Nombre de pages à l’aide de ce processus dans le fichier d’échange actuel. Le fichier de pagination stocke les pages de données utilisées par le processus mais non contenues dans d’autres fichiers. Le fichier d’échange est utilisé par tous les processus et un manque d’espace dans le fichier d’échange peut provoquer des erreurs pendant l’exécutant des autres processus.|  
|**Octets de fichier d’échange maximale**|Le nombre maximal de pages que ce processus a utilisée dans le fichier d’échange.|  
|**Défauts de page**|Le nombre de défauts de Page par les threads s’exécutant dans ce processus. Une erreur de page se produit lorsqu’un thread fait référence à une page de mémoire virtuelle qui n’est pas dans son jeu de travail dans la mémoire principale. Par conséquent, la page ne sera pas être récupérée à partir du disque s’il s’agit de la liste d’attente et donc déjà dans la mémoire principale, ou si elle est utilisée par un autre processus avec lequel la page est partagée.|