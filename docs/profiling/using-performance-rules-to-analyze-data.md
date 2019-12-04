---
title: Utilisation des règles de performances pour analyser des données | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f5af6b366a1181187c23327449ade8e03e30107f
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778061"
---
# <a name="use-performance-rules-to-analyze-data"></a>Utiliser des règles de performance pour analyser des données
Les avertissements de performances des outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] signalent les problèmes qui surviennent dans une application profilée et qui peuvent ralentir l’exécution du programme. Les avertissements peuvent également vous informer que vous devez changer de méthode de collecte pour collecter des données plus utiles. Les avertissements de performances sont générés automatiquement dans une session de profilage. Les avertissements s’affichent dans la fenêtre **Liste d’erreurs** quand un fichier de données de profilage est ouvert dans Visual Studio. Dans la fenêtre **Liste d’erreurs**, vous pouvez localiser le code source du problème et vous pouvez afficher des informations détaillées sur l’erreur, comme des informations sur la façon de résoudre le problème. Vous pouvez également désactiver les avertissements qui ne vous n’intéressent pas.

> [!NOTE]
> Les avertissements de performances du profileur sont générés par l’analyse dynamique de l’exécution du programme et sont indépendants des avertissements d’analyse du code. L’analyse du code peut également générer des avertissements de performances pour le code managé en fonction de l’analyse statique du code source. Pour plus d’informations, consultez [Analyser la qualité du code managé](../code-quality/code-analysis-for-managed-code-overview.md) et [Avertissements de performance](../code-quality/performance-warnings.md).

## <a name="in-this-section"></a>Dans cette section
- [Guide pratique pour afficher les avertissements liés aux performances](../profiling/how-to-view-performance-warnings.md)

 Fournit des informations sur la façon d’ouvrir la fenêtre **Liste d’erreurs** pour afficher les avertissements de performances du profileur.

- [Guide pratique pour configurer les règles de performance](../profiling/how-to-configure-performance-rules.md)

 Fournit des informations sur la façon d’activer ou de désactiver les avertissements de performances individuels.

- [Informations de référence sur les règles de performance](../profiling/performance-rules-reference.md)

 Fournit des informations détaillées les avertissements de performances du profileur
