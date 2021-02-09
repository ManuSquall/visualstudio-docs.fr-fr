---
title: Navigateur d’utilisation | Microsoft Docs
description: Découvrez comment vous pouvez utiliser le navigateur d’utilisation dans le visualiseur concurrentiel pour sélectionner un intervalle de temps dans une trace.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d92747bb90cae18a79e81e49689ce8c01b8a9b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917574"
---
# <a name="utilization-navigator"></a>Navigateur d'utilisation
Vous pouvez utiliser le navigateur d’utilisation dans le visualiseur concurrentiel pour sélectionner un intervalle de temps dans une trace. Le visualiseur concurrentiel montre l’utilisation des cœurs de l’UC par processus cible au fil du temps. Ceci facilite l’examen des modèles d’utilisation de l’UC et permet également de comparer les données d’utilisation et les données d’autres vues. Le navigateur d’utilisation apparaît en haut de chaque vue dans le visualiseur concurrentiel. L’illustration suivante montre le navigateur d’utilisation.

 ![Navigateur d’utilisation présentant la période sélectionnée](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator") Navigateur d’utilisation et intervalle de temps sélectionné

 Dans l’illustration, l’intervalle sélectionné est défini par un rectangle rouge, appelé *curseur de position*.

 Voici comment vous pouvez utiliser le navigateur d’utilisation pour manipuler la plage de temps affichée :

- Vous pouvez effectuer un panoramique en faisant glisser le curseur de position vers la gauche ou la droite. (Clavier : déplacez le focus sur le curseur de position et appuyez sur la touche de direction gauche ou droite.)

- Vous pouvez modifier l’étendue de l’intervalle en faisant glisser une des poignées. (Clavier : déplacez le focus sur une poignée et appuyez sur la touche de direction gauche ou droite.)

  Si vous modifiez l’intervalle à l’aide d’un autre contrôle de zoom du visualiseur concurrentiel, le navigateur d’utilisation se met à jour de façon à refléter les modifications.