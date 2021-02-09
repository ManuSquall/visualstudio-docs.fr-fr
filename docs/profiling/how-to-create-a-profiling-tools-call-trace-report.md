---
title: Créer un rapport de suivi des appels des Outils de profilage | Microsoft Docs
description: Créez un rapport de suivi d’appels des outils de performances pour consulter les informations de minutage de vos fonctions et des fonctions appelées par vos fonctions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 12d294202c3cea2c19f4f88ca4e7bd1dfd62df67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860826"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Guide pratique pour créer un rapport de suivi d’appels des Outils de profilage
Le *rapport de suivi des appels* des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] liste les informations chronologiques de chaque point d’entrée et de sortie des fonctions de votre application, et de chaque appel effectué par votre fonction à d’autres fonctions. Les rapports de suivi des appels sont disponibles pour les données de profilage seulement si elles ont été collectées avec la méthode d’instrumentation.

> [!NOTE]
> Vous ne pouvez pas afficher des rapports de suivi des appels dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous devez utiliser l’outil en ligne de commande **VSPerfReport** pour générer une valeur séparée par des virgules (.*CSV*) ou. fichier *XML* . Pour plus d’informations sur cet outil, consultez [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Pour créer un rapport de suivi des appels

1. Ouvrez une fenêtre d' **invite de commandes** .

2. Saisissez ensuite la commande suivante dans l’invite de commandes :

     *chemin_outils* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |Élément|Description|
    |-|-|
    |*chemin_outils*|Chemin des outils en ligne de commande des Outils de profilage. Pour plus d’informations, consultez [Spécifier le chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*fichier_VSP*|Données de profilage (.*vsp* ou. *vsps*) txt. Les chemins complets et partiels sont acceptés.|
    |Xml|Génère un rapport au format XML.|

## <a name="see-also"></a>Voir aussi
- [Comment : collecter des données Suivi d’v nements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [API des outils de profilage](../profiling/profiling-tools-apis.md)
