---
title: 'Procédure : Collecter les données de suivi d’événements pour Windows (ETW) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9734c75f078380649009d10da13ed8c926e5e16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973862"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Procédure : Collecter les données de suivi d’événements pour Windows (ETW)

Le suivi d’événements pour Windows (ETW) est une fonctionnalité de traçage efficace de niveau noyau qui permet de journaliser les événements de noyau et les événements définis par l’application du profileur. Les données collectées à partir du fournisseur d’événements ne peuvent être affichées qu’à l’aide de l’option /**Summary:ETW** de l’outil en ligne de commande [VSPerfReport](../profiling/vsperfreport.md). Vous pouvez utiliser ce rapport pour déterminer où se situent les problèmes de performances au sein de l’application.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Pour activer les fournisseurs de suivi d’événements

1. Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.

2. Dans les **Pages de propriétés**, cliquez sur les propriétés **Événements Windows**.

3. Dans la liste **Sélectionner les fournisseurs de suivi d’événements desquels collecter des données**, sélectionnez les fournisseurs d’événements que vous voulez utiliser pour profiler votre application.

## <a name="see-also"></a>Voir aussi

[Configurer des sessions de performances](../profiling/configuring-performance-sessions.md)