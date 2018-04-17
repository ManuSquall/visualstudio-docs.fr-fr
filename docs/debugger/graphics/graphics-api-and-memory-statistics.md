---
title: API des graphiques et des statistiques de la mémoire | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b57edb59984537638dd32b621406775087ba680e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="graphics-api-and-memory-statistics"></a>API des graphiques et des statistiques de la mémoire
<!-- VERSIONLESS -->
Visual Studio 2017 et une prise en charge les statistiques d’API graphiques et outils de statistiques de la mémoire.  Ces deux outils vous permettent d’afficher des divers éléments d’informations sur l’utilisation de l’API de Direct3D, ainsi que la consommation de mémoire GPU de diverses ressources.

## <a name="graphics-api-statistics"></a>Statistiques des API graphiques
Les statistiques d’API graphiques dans Visual Studio Graphics Diagnostics vous permet d’afficher tous les appels Direct3D qui ont été apportées et le nombre de chaque appel.  Pour afficher la fenêtre, sélectionnez le **vue > API statistiques** élément de menu.

![Statistiques de l’API](media/gfx_diag_api_statistics.png)

Cet outil peut être pratique dans la détection des appels DirectX que vous ne réalisent pas forcément vous apportez, ou des appels que font trop souvent.

Vous pouvez avec le bouton droit dans la fenêtre pour copier toutes les données au format CSV, qui peut être collé dans quelque chose comme Excel pour une analyse plus approfondie.

## <a name="memory-statistics"></a>Statistiques de la mémoire
Cet outil affiche la quantité de mémoire alloue le pilote graphique pour les ressources que vous créez dans un frame.  Pour afficher cette fenêtre, sélectionnez le **vue > statistiques de la mémoire** élément de menu.

![Statistiques de la mémoire](media/gfx_diag_memory_statistics.png)

Le **GPU Allocation** colonne affiche la quantité de mémoire utilisée par les événements affichés dans le **événement** colonne.  Vous pouvez également sélectionner l’icône espion ![icône espion](media/gfx_watch.png) pour afficher les [l’historique des ressources](graphics-event-list.md#resource-history) pour l’événement sélectionné.

Comme avec l’outil de statistiques de l’API, vous pouvez avec le bouton droit dans la fenêtre pour copier toutes les données au format CSV, qui peut être collé dans quelque chose comme Excel pour une analyse plus approfondie.

## <a name="see-also"></a>Voir aussi  
[Graphics Diagnostics (débogage DirectX Graphics)](visual-studio-graphics-diagnostics.md)   
[Historique des ressources](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->