---
title: Rapport Opérations sur le disque (Vue Threads) | Microsoft Docs
description: Le rapport Opérations sur le disque affiche les opérations d’E/S de disque effectuées dans les canaux de disques. Consultez les informations qui sont signalées pour chaque accès au disque.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44975999c71b1c331d90aa10f709071cef466cb1
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686530"
---
# <a name="disk-operations-report-threads-view"></a>Rapport sur les opérations sur le disque (Vue Threads)
Le rapport Opérations sur le disque affiche les opérations d’E/S de disque effectuées dans les canaux de disques.

 Les informations suivantes sont signalées pour chaque accès au disque effectué pour le compte du processus en cours de profilage dans la fenêtre de temps actuellement visible :

- Le nom et le PID du processus qui a accédé au disque

- L’ID du thread qui a accédé au disque

- Le nom du fichier ayant fait l’objet d’un accès

- Le nombre de lectures par fichier

- Le nombre d’octets lus

- La latence de lecture, en millisecondes

- Le nombre d’écritures

- Le nombre d’octets écrits

- La latence d’écriture, en millisecondes

## <a name="see-also"></a>Voir aussi
- [vue Threads](../profiling/threads-view-parallel-performance.md)