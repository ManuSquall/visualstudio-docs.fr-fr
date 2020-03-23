---
title: Suivi des événements pour Windows (ETW), rapport | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 19412d184377637c29f34b2fe3ffd033f176b97c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779296"
---
# <a name="event-tracing-for-windows-etw-report"></a>Suivi des événements pour Windows (ETW), rapport
Le rapport Suivi des événements pour Windows (ETW) liste les événements ETW enregistrés dans une session de performances des Outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les données ETW sont collectées dans un binaire (.* etl*) fichier.

> [!NOTE]
> Vous ne pouvez pas afficher les rapports de suivi des événements pour Windows dans l’interface de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Pour plus d’informations sur la façon de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] collecter ETW en utilisant les outils de profilage à partir de l’interface, voir [Comment : Collecter des données de traçage d’événements pour Windows (ETW).](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

- Pour plus d’informations sur la collecte des données de suivi des événements pour Windows en utilisant les outils de ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), consultez [Événements](../profiling/events-vsperfcmd.md).

- Vous générez le rapport de suivi d’événements pour Windows en utilisant la commande **VSReport/Summary:ETW**. Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).

|Colonne|Description|
|------------|-----------------|
|**Timestamp**|Identifie quand l’événement s’est produit.|
|**ID du processus**|Identifie le processus qui a généré l’événement.|
|**ID du thread**|Identifie le thread qui a généré l’événement.|
|**Description**|Identifie le fournisseur d’événements.|
|**Type**|Identifie le type d’événement.|
|**Propriétés**|Propriétés de l’événement. Chaque événement est une paire nom-valeur avec la virgule comme séparateur, qui est placée entre des crochets.|
