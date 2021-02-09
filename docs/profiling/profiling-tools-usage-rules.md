---
title: Règles d’utilisation des outils de profilage | Microsoft Docs
description: Découvrez comment les règles de performances de la catégorie utilisation Outils de profilage fournissent des conseils sur l’utilisation du profileur pour collecter les données le plus efficacement possible.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2514d6893c205a1c48c76983c859528be6ad938b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861619"
---
# <a name="profiling-tools-usage-rules"></a>Règles d'utilisation des outils de profilage
Les règles de performance de la catégorie d’utilisation des outils de profilage fournissent des conseils sur l’utilisation du profileur pour collecter des données de manière plus efficace.

| Règle | Description |
| - | - |
| [DA0002 : VSPerfCorProf.dll est manquant](../profiling/da0002-vsperfcorprof-dll-is-missing.md) | Le profilage en ligne de commande peut contenir des données incomplètes pour les fichiers binaires .NET. Cela peut arriver si vous n’avez pas défini les bonnes variables d’environnement. |
| [DA0003 : Nombreux échantillons de noyau](../profiling/da0003-many-kernel-samples.md) | De nombreux échantillons de profilage qui se sont produits en dehors de l’exécution du fichier binaire cible ont été enregistrés. Pour collecter des données plus précises, utilisez la méthode d’instrumentation. |
| [DA0004 : Utilisation intensive du processeur](../profiling/da0004-high-processor-usage.md) | Les données de profilage suggèrent que vos processeurs étaient régulièrement occupés pendant l’exécution du profilage. Pour collecter des données plus précises, utilisez la méthode d’échantillonnage. |
| [DA0008 : Peu d’échantillons collectés](../profiling/da0008-few-samples-collected.md) | Le nombre d’échantillons collectés dans le cadre de l’exécution du profilage n’était pas assez élevé pour être statistiquement significatif. Effectuez à nouveau le profilage et exécutez l’application pendant une plus longue durée. Vous pouvez également utiliser la méthode d’instrumentation pour collecter des données. |
| [DA0026 : Traitement temps CPU noyaux excessif](../profiling/da0026-excessive-kernel-cpu-time-processing.md) | Une durée significative s’est écoulée en mode noyau de processeur dans le cadre de l’exécution du profilage. Effectuez l’échantillonnage en utilisant les appels système plutôt que le temps comme métrique. |
| [DA0029 : Version CLR non prise en charge](../profiling/da0029-unsupported-clr-version.md) | Le fichier binaire profilé utilise une version du .NET Framework qui n’est pas prise en charge par le profileur. Les rapports du profileur ne peuvent pas résoudre les noms de symboles. |
| [DA0030 : Collecter les mesures d’interaction de couche pour les projets de base de données](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md) | Un nombre significatif d’appels à des méthodes dans l’espace de noms <xref:System.Data?displayProperty=fullName> ont été collectés. Pour inclure les données relatives aux appels de base de données, collectez les données d’interaction de couche dans vos exécutions de profil. |
