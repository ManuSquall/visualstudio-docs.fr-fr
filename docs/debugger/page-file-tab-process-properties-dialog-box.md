---
title: Onglet fichier d’échange de la boîte de dialogue Propriétés du processus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25dc3b0aca1b58c18ae4038540c14fc4dbfe4036
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62904105"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Onglet Fichier d'échange de la boîte de dialogue Propriétés du processus
Utilisez l’onglet **fichier** d’échange pour examiner le fichier d’échange d’un processus. Pour afficher la [boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md), déplacez le focus vers une fenêtre [vue processus](../debugger/processes-view.md) . Sélectionnez un nœud de processus dans l’arborescence, puis choisissez **Propriétés** dans le menu **affichage** .

 Les paramètres suivants sont disponibles sous l’onglet **fichier d’échange** :

|Entrée|Description|
|-----------|-----------------|
|**Octets de fichier d’échange**|Nombre actuel de pages que ce processus utilise dans le fichier d’échange. Le fichier d’échange stocke des pages de données utilisées par le processus, mais qui ne sont pas contenues dans d’autres fichiers. Le fichier d’échange est utilisé par tous les processus, et l’espace insuffisant dans le fichier d’échange peut entraîner des erreurs pendant l’exécution d’autres processus.|
|**Nombre d’octets de fichier d’échange max.**|Nombre maximal de pages que ce processus a utilisées dans le fichier d’échange.|
|**Erreurs de page**|Nombre de défauts de page par les threads qui s’exécutent dans ce processus. Un défaut de page se produit lorsqu'un thread fait référence à une page de mémoire virtuelle qui n'est pas dans son jeu de travail dans la mémoire principale. Par conséquent, la page n’est pas récupérée à partir du disque si elle se trouve dans la liste d’attente, et donc déjà dans la mémoire principale, ou si elle est utilisée par un autre processus avec lequel la page est partagée.|