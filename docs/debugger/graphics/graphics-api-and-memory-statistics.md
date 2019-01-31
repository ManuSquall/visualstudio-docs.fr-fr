---
title: API des graphiques et des statistiques de la mémoire | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0c1ed6e2fdd461b0fdf502c01089aeafd9a87cb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925628"
---
# <a name="graphics-api-and-memory-statistics"></a>API des graphiques et des statistiques de la mémoire
<!-- VERSIONLESS --> Visual Studio 2017 et supérieur prennent en charge les outils graphiques statistiques d’API et les statistiques de la mémoire.  Ces deux outils vous permettent d’afficher des divers éléments d’informations sur l’utilisation de l’API de Direct3D, ainsi que la consommation de mémoire GPU de diverses ressources.

## <a name="graphics-api-statistics"></a>Statistiques d’API graphiques
Les statistiques d’API graphiques dans Visual Studio Graphics Diagnostics vous permet d’afficher tous les appels Direct3D qui ont été apportées et le nombre de chaque appel.  Pour afficher la fenêtre, sélectionnez le **Afficher > statistiques d’API** élément de menu.

![Statistiques d’API](media/gfx_diag_api_statistics.png)

Cet outil peut être pratique dans la découverte des appels DirectX que vous en apercevoir vous effectuez des appels et que font trop souvent.

Vous pouvez avec le bouton droit dans la fenêtre pour copier toutes les données en tant que fichier CSV, ce qui peut être collé dans quelque chose comme Excel pour une analyse plus approfondie.

## <a name="memory-statistics"></a>Statistiques de la mémoire
Cet outil affiche la quantité de mémoire du pilote d’affichage est alloue pour les ressources que vous créez dans un frame.  Pour afficher cette fenêtre, sélectionnez le **Afficher > statistiques de la mémoire** élément de menu.

![Statistiques de la mémoire](media/gfx_diag_memory_statistics.png)

Le **Allocation GPU** colonne affiche la quantité de mémoire utilisée par l’événement affiché dans le **événement** colonne.  Vous pouvez également sélectionner l’icône espion ![icône espion](media/gfx_watch.png) pour afficher le [historique des ressources](graphics-event-list.md#resource-history) pour l’événement sélectionné.

Comme avec l’outil de statistiques d’API, vous pouvez avec le bouton droit dans la fenêtre pour copier toutes les données en tant que fichier CSV, ce qui peut être collé dans quelque chose comme Excel pour une analyse plus approfondie.

## <a name="see-also"></a>Voir aussi  
[Graphics Diagnostics (débogage DirectX Graphics)](visual-studio-graphics-diagnostics.md)   
[Historique des ressources](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->