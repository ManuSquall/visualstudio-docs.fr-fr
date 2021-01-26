---
title: Créer un rapport Suivi d’événements pour Windows (ETW) des outils de profilage | Microsoft Docs
description: Découvrez comment créer un rapport de Suivi d’v nements pour Windows (ETW). Elle répertorie les événements ETW enregistrés dans une session de performance Visual Studio Outils de profilage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c35a3e2d7da9472167c2ac20400fe3b3992b4883
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800485"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Guide pratique pour créer un rapport de suivi d’événements pour Windows (ETW) des outils de profilage
Le rapport Suivi d’événements pour Windows (ETW) répertorie les événements de suivi d’événements pour Windows enregistrés dans une session de performances des outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les données ETW sont collectées dans un fichier binaire (.*fichier ETL*). Pour plus d’informations sur ce rapport, consultez le [rapport suivi d’v nements pour Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> Vous ne pouvez pas afficher les rapports de suivi d’événements pour Windows dans l’interface pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Pour plus d’informations sur la collecte des données ETW à l’aide de l’interface pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , consultez [Comment : collecter des données suivi d’V nements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Pour plus d’informations sur la collecte des données de suivi d’événements pour Windows à partir d’une invite de commandes, consultez [VSPerfCmd](../profiling/vsperfcmd.md) et [Événements](../profiling/events-vsperfcmd.md).

  Vous générez le rapport ETW à l’aide de la commande **VSReport/Summary : ETW** . La. *ETL* qui contient les données ETW doit se trouver dans le même répertoire que les données de profilage (.*vsp* ou. *vsps*) txt. Par défaut, le rapport est généré sous la forme d’une valeur séparée par des virgules (.*CSV*). Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Pour générer un rapport Suivi d’événements pour Windows

- Dans une fenêtre **Invite de commandes**, exécutez la commande suivante :

     *chemin_outils* **VSPerfReport** *fichier_VSP*  **/Summary:ETW [/Xml]**

    |Élément|Description|
    |-|-|
    |*chemin_outils*|Chemin de l’utilitaire Outils de profilage. Pour plus d’informations, consultez [Spécifier le chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*fichier_VSP*|Données de profilage (.*vsp* ou. *vsps*) txt. Les chemins complets et partiels sont acceptés.|
    |Xml|Génère un rapport au format XML.|
