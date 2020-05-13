---
title: Guide pratique pour créer un rapport Suivi d’événements pour Windows (ETW) des outils de profilage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ce7b02be682d825205fc5fa50d07c1ca817a24d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776399"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Guide pratique pour créer un rapport de suivi d’événements pour Windows (ETW) des outils de profilage
Le rapport Suivi d’événements pour Windows (ETW) répertorie les événements de suivi d’événements pour Windows enregistrés dans une session de performances des outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les données ETW sont collectées dans un binaire (.* etl*) fichier. Pour plus d’informations sur ce rapport, voir [Le rapport Event Tracing for Windows (ETW).](../profiling/event-tracing-for-windows-etw-report.md)

> [!NOTE]
> Vous ne pouvez pas afficher les rapports de suivi d’événements pour Windows dans l’interface pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Pour plus d’informations sur la façon [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]de collecter des données ETW en utilisant l’interface pour , voir [Comment: Collect Event Tracing pour Windows (ETW) données](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Pour plus d’informations sur la collecte des données de suivi d’événements pour Windows à partir d’une invite de commandes, consultez [VSPerfCmd](../profiling/vsperfcmd.md) et [Événements](../profiling/events-vsperfcmd.md).

  Vous générez le rapport ETW en utilisant la commande **VSReport/summary:etw.** Lla. *etl* qui contient les données ETW doit être dans le même répertoire que les données de profilage (.* vsp* ou . *vsps*) Fichier. Par défaut, le rapport est généré en valeur séparée par virgule (.* csv*) fichier. Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Pour générer un rapport Suivi d’événements pour Windows

- Dans une fenêtre **Invite de commandes**, exécutez la commande suivante :

     *chemin_outils* **VSPerfReport** *fichier_VSP*  **/Summary:ETW [/Xml]**

    |||
    |-|-|
    |*chemin_outils*|Chemin de l’utilitaire Outils de profilage. Pour plus d’informations, consultez [Spécifier le chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*fichier_VSP*|Les données de profilage (.* vsp* ou . *vsps*) Fichier. Les chemins complets et partiels sont acceptés.|
    |Xml|Génère un rapport au format XML.|
