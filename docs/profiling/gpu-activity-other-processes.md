---
title: Activité GPU (autres processus) | Microsoft Docs
description: En savoir plus sur les segments activité GPU (autres processus) dans la vue threads du visualiseur concurrentiel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71ecb1587545120aef8e18ce847d5e957f3e3cdd
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801312"
---
# <a name="gpu-activity-other-processes"></a>Activité GPU (autres processus)
Les segments **Activité GPU (autres processus)** de la vue Threads du visualiseur concurrentiel représentent les périodes auxquelles le GPU a traité des demandes pour le compte d’autres processus du système. Ces demandes sont envoyées au GPU sous forme de paquets d’accès direct à la mémoire (DMA).  La longueur d’un segment représente la durée pendant laquelle le paquet a été traité par le GPU.

 Lorsque vous sélectionnez ce type de segment, le rapport sous l’onglet **Actuel** affiche des informations sur le paquet qui a été traité.  Ces informations incluent la durée pendant laquelle le paquet a attendu dans la file d’attente matérielle associée au moteur DirectX, le processus qui a envoyé le paquet, ainsi que le temps nécessaire pour traiter le paquet.