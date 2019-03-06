---
title: 'DA0014 : Taux très élevés de pagination de la mémoire active sur le disque | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f6486fc204942553a58e437d56fc7d0ffee548b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630390"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014 : Taux très élevés de pagination de la mémoire active sur le disque

|||
|-|-|
|ID de règle|DA0014|
|Category|Mémoire et pagination|
|Méthode de profilage|Tous|
|Message|Taux très élevé de pagination de la mémoire active sur le disque. Votre application peut être liée à la mémoire.|
|Type de règle|Warning|

 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 25 échantillons pour déclencher cette règle.

## <a name="cause"></a>Cause
 Les données de performances système qui ont été collectées durant l’exécution du profilage indiquent qu’un taux très élevé de pagination de la mémoire active vers et depuis le disque a été relevé pendant toute la durée de l’exécution du profilage. De tels taux de pagination affectent généralement les performances et la réactivité de l’application. Réduisez les allocations de mémoire en modifiant les algorithmes. Envisagez également de revoir les besoins en mémoire de votre application. Réexécutez le profilage sur un ordinateur disposant de davantage de mémoire.

## <a name="rule-description"></a>Description de la règle
 Une pagination excessive sur le disque peut être due à un manque de mémoire physique. Si les opérations de pagination utilisent une grande partie du disque physique sur lequel réside le fichier de pagination, elles peuvent ralentir d’autres opérations de disque orientées application effectuées sur le même disque.

 Il arrive fréquemment que les pages soient lues ou écrites sur le disque lors d’opérations de pagination en bloc. Le nombre de pages en sortie/s est souvent beaucoup plus élevé que le nombre d’écritures de pages/s, par exemple. Cela est dû au fait que les pages en sortie/s comprennent également les pages de données modifiées dans le cache de fichiers système. Toutefois, il n’est pas toujours facile de déterminer quel processus est directement responsable de la pagination, ni de connaître la cause de cette pagination.

> [!NOTE]
>  Cette règle se déclenche lorsque les niveaux de pagination de la mémoire active atteignent un taux très élevé. Quand le niveau de pagination est significatif, mais pas extrême, la règle à caractère informatif [DA0017 : Taux élevés de pagination de la mémoire active sur le disque](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md) est déclenchée à la place.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la vue [Marques](../profiling/marks-view.md). Recherchez la colonne **Mémoire\Pages/s**. Déterminez s’il existe des phases spécifiques de l’exécution du programme durant lesquelles l’activité d’E/S de pagination est plus importante.

 Si vous collectez des données de profil pour une application ASP.NET dans un scénario de test de charge, essayez de réexécuter le test de charge sur un ordinateur configuré avec de la mémoire physique (ou RAM) supplémentaire.

 Envisagez de réduire les allocations de mémoire en modifiant les algorithmes et en évitant les API nécessitant beaucoup de mémoire, telles que String.Concat et String.Substring.