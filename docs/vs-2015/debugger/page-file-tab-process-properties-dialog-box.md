---
title: Onglet fichier d’échange, boîte de dialogue Propriétés de processus | Microsoft Docs
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
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fa1eba7af60638d82c791958af6bf66a3272242
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506430"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Onglet Fichier d'échange de la boîte de dialogue Propriétés du processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [onglet de fichier de Page, la boîte de dialogue Propriétés du processus](https://docs.microsoft.com/visualstudio/debugger/page-file-tab-process-properties-dialog-box).  
  
Utilisez le **fichier d’échange** onglet pour examiner le fichier de pagination d’un processus. Pour afficher le [boîte de dialogue Propriétés de processus](../debugger/process-properties-dialog-box.md), déplacez le focus à un [vue processus](../debugger/processes-view.md) fenêtre. Sélectionnez n’importe quel nœud de processus dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **fichier d’échange** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Octets de fichier d’échange**|Le nombre actuel de pages à l’aide de ce processus dans le fichier d’échange. Le fichier de pagination stocke les pages de données utilisées par le processus mais non contenues dans d’autres fichiers. Le fichier d’échange est utilisé par tous les processus et le manque d’espace dans le fichier d’échange peut provoquer des erreurs pendant l’exécutant des autres processus.|  
|**Octets de fichier d’échange maximale**|Le nombre maximal de pages que ce processus a utilisé dans le fichier d’échange.|  
|**Défauts de page**|Le nombre de défauts de Page par les threads s’exécutant dans ce processus. Un défaut de page se produit lorsqu’un thread fait référence à une page de mémoire virtuelle qui n’est pas dans son jeu de travail dans la mémoire principale. Par conséquent, la page ne sera pas être récupérée à partir du disque s’il s’agit de la liste d’attente et donc déjà dans la mémoire principale, ou si elle est utilisée par un autre processus avec lequel la page est partagée.|



