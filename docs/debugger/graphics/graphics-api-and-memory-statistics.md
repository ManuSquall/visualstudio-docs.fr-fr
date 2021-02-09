---
title: Statistiques de la mémoire et de l’API Graphics | Microsoft Docs
description: Passez en revue les outils statistiques de l’API Graphics et statistiques de la mémoire, qui présentent des informations sur l’utilisation de l’API Direct3D et la consommation de mémoire GPU de diverses ressources.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 08c9f518f6d56f2ec211ef494da3890a56bf1369
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882295"
---
# <a name="graphics-api-and-memory-statistics"></a>Statistiques de la mémoire et de l’API Graphics
<!-- VERSIONLESS -->
Visual Studio 2017 et versions ultérieures prennent en charge les outils statistiques de l’API Graphics et statistiques de mémoire.  Ces deux outils vous permettent d’afficher différents bits d’informations sur l’utilisation de l’API Direct3D, ainsi que la consommation de mémoire GPU de diverses ressources.

## <a name="graphics-api-statistics"></a>Statistiques de l’API Graphics
Les statistiques de l’API Graphics dans Visual Studio Graphics Diagnostics vous permettent d’afficher tous les appels Direct3D effectués et le nombre de chaque appel.  Pour afficher la fenêtre, sélectionnez l’élément de menu **afficher > statistiques** de l’API.

![Statistiques d’API](media/gfx_diag_api_statistics.png)

Cet outil peut être pratique pour découvrir les appels DirectX que vous n’êtes pas en train d’effectuer, ou les appels que vous faites trop souvent.

Vous pouvez cliquer avec le bouton droit dans la fenêtre pour copier toutes les données au format CSV, qui peuvent être collées dans des éléments tels qu’Excel pour une analyse plus poussée.

## <a name="memory-statistics"></a>Statistiques de la mémoire
Cet outil affiche la quantité de mémoire allouée par le pilote graphique pour les ressources que vous créez dans un frame.  Pour afficher cette fenêtre, sélectionnez l’élément de menu Afficher les statistiques de la **mémoire >** .

![Statistiques de la mémoire](media/gfx_diag_memory_statistics.png)

La colonne **allocation GPU** affiche la quantité de mémoire utilisée par l’événement affiché dans la colonne d' **événement** .  Vous pouvez également sélectionner l’icône espion icône ![ Espion ](media/gfx_watch.png) pour afficher l' [historique des ressources](graphics-event-list.md#resource-history) de l’événement sélectionné.

Comme avec l’outil statistiques des API, vous pouvez cliquer avec le bouton droit dans la fenêtre pour copier toutes les données au format CSV, qui peuvent être collées dans des éléments tels qu’Excel pour une analyse plus poussée.

## <a name="see-also"></a>Voir aussi
- [Graphics Diagnostics (débogage DirectX Graphics)](visual-studio-graphics-diagnostics.md)
- [Historique des ressources](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->