---
title: Segment de chronologie vide | Microsoft Docs
description: Dans le visualiseur concurrentiel Visual Studio, comprenez la raison pour laquelle une section d’une chronologie peut être vide (a un arrière-plan blanc) pour un type de canal.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a4a3265c3b31653d94a686fa8fda12f7699596e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955266"
---
# <a name="empty-timeline-segment"></a>Segment de chronologie vide
Dans le visualiseur concurrentiel, la raison d’un segment de chronologie vide (avec un arrière-plan blanc) dépend du type de canal.

- Pour un canal de thread d’UC, cela signifie que le thread n’existait pas à cette période. Pour en savoir plus sur le thread, regardez sa section d’exécution en utilisant le contrôle de zoom ou en faisant défiler la page horizontalement.

- Pour un canal d’E/S, cela signifie qu’aucun accès disque ne s’est produit pour le compte du processus cible à ce moment précis.

- Pour un canal DirectX, cela signifie qu’aucun travail GPU n’a été effectué pour le compte du processus cible pendant cette période.

- Pour un canal de marqueur, cela signifie qu’aucun marqueur n’a été généré.

## <a name="see-also"></a>Voir aussi
- [vue Threads](../profiling/threads-view-parallel-performance.md)
- [Contrôle zoom (vue threads)](../profiling/zoom-control-threads-view.md)