---
title: Suivi des événements pour Windows (ETW), rapport | Microsoft Docs
description: En savoir plus sur le rapport Suivi d’v nements pour Windows (ETW), qui répertorie les événements ETW enregistrés dans une session de performance de Visual Studio Outils de profilage.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e7167f2fb5c78a6fa8c3d83fb56c2c2eba217516
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801417"
---
# <a name="event-tracing-for-windows-etw-report"></a>Suivi des événements pour Windows (ETW), rapport
Le rapport Suivi des événements pour Windows (ETW) liste les événements ETW enregistrés dans une session de performances des Outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les données ETW sont collectées dans un fichier binaire (.*fichier ETL*).

> [!NOTE]
> Vous ne pouvez pas afficher les rapports de suivi des événements pour Windows dans l’interface de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Pour plus d’informations sur la collecte d’événements ETW à l’aide de la Outils de profilage à partir de l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interface, consultez [Comment : collecter des données de suivi d’V nements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Pour plus d’informations sur la collecte des données de suivi des événements pour Windows en utilisant les outils de ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), consultez [Événements](../profiling/events-vsperfcmd.md).

- Vous générez le rapport de suivi d’événements pour Windows en utilisant la commande **VSReport/Summary:ETW**. Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).

|Colonne|Description|
|------------|-----------------|
|**Timestamp**|Identifie quand l’événement s’est produit.|
|**ID de processus**|Identifie le processus qui a généré l’événement.|
|**ID du thread**|Identifie le thread qui a généré l’événement.|
|**Description**|Identifie le fournisseur d’événements.|
|**Type**|Identifie le type d’événement.|
|**Propriétés**|Propriétés de l’événement. Chaque événement est une paire nom-valeur avec la virgule comme séparateur, qui est placée entre des crochets.|
