---
title: Collecter les données des compteurs Windows | Microsoft Docs
description: Les compteurs Windows sont utilisés dans le profilage par instrumentation. Découvrez Comment collecter des données de compteurs Windows et comment limiter l’analyse à un intervalle de collecte unique.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ccbdf9afb843c8bdac2d904dc22375a4a69e733a
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801042"
---
# <a name="how-to-collect-windows-counter-data"></a>Guide pratique pour collecter les données des compteurs Windows

Les compteurs Windows sont des compteurs de performances système dont les données peuvent être collectées à intervalles réguliers pendant le profilage. Dans la vue Marques du rapport Outils de profilage, une ligne est étiquetée **AutoMark** pour chaque intervalle de collecte. Cette ligne contient des colonnes qui décrivent les valeurs de compteur de performances avec cet intervalle. Pour limiter l’analyse à un laps de temps entre deux marques particulières, sélectionnez les marques, cliquez avec le bouton droit, puis sélectionnez **Filtrer par**  >  **marques** dans le menu contextuel.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Pour collecter les données des compteurs Windows

1. Dans l’Explorateur de performances, cliquez avec le bouton droit sur la session pour laquelle vous voulez configurer des compteurs Windows, puis sélectionnez **Propriétés**.

2. Dans les **Pages de propriétés**, cliquez sur **Compteurs Windows**.

3. Cochez la case **Collecter les compteurs Windows**.

4. Dans la zone de texte **Intervalle de collecte (ms)**, tapez un intervalle.

5. Sélectionnez une catégorie dans la liste déroulante **Catégorie de compteurs**.

6. Sélectionnez une instance dans la liste déroulante **Instance**.

7. Sélectionnez les compteurs que vous voulez utiliser pour profiler votre application.

8. Cliquez sur **appliquer.**

## <a name="see-also"></a>Voir aussi

[Configurer des sessions](../profiling/configuring-performance-sessions.md) 
 de performance Propriétés de la [session de performance](../profiling/performance-session-properties.md) 
 [Compteurs UC et Windows](../profiling/cpu-and-windows-counters.md)
