---
title: DA0017-taux élevés de pagination de la mémoire active sur le disque | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dfaeedc52e7d6b2888415200e7dccf258fa96d5c
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85327952"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017 : Taux élevés de pagination de la mémoire active sur le disque

|||
|-|-|
|ID de règle|DA0017|
|Category|Mémoire et pagination|
|Méthode de profilage|Tous|
|Message|Taux élevé de pagination de la mémoire active sur le disque. Votre application peut être liée à la mémoire.|
|Type de règle|Information|

 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.

## <a name="cause"></a>Cause
 Les données de performances système qui ont été collectées durant l’exécution du profilage indiquent qu’un taux élevé de pagination de la mémoire active vers et depuis le disque a été relevé pendant toute la durée de l’exécution du profilage. De tels taux de pagination affectent généralement les performances et la réactivité de l’application. Réduisez les allocations de mémoire en modifiant les algorithmes. Envisagez également de revoir les besoins en mémoire de votre application.

## <a name="rule-description"></a>Description de la règle

> [!NOTE]
> Cette règle à caractère informatif se déclenche lorsque les niveaux de pagination de la mémoire active atteignent un taux élevé. Lorsqu’un niveau très élevé de pagination se produit, la règle d’avertissement [DA0014 : Taux très élevés de pagination de la mémoire active sur le disque](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) est déclenchée.

 Une pagination excessive sur le disque peut être due à un manque de mémoire physique. Si les opérations de pagination utilisent une grande partie du disque physique sur lequel réside le fichier de pagination, elles peuvent ralentir d’autres opérations de disque orientées application effectuées sur le même disque.

 Il arrive fréquemment que les pages soient lues ou écrites sur le disque lors d’opérations de pagination en bloc. Le nombre de pages en sortie/s est souvent beaucoup plus élevé que le nombre d’écritures de pages/s, par exemple. Cela est dû au fait que les pages en sortie/s comprennent également les pages de données modifiées dans le cache de fichiers système. Toutefois, il n’est pas toujours facile de déterminer quel processus est directement responsable de la pagination, ni de connaître la cause de cette pagination.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la vue [marques](../profiling/marks-view.md) . Recherchez la colonne **Mémoire\Pages/s**. Déterminez s’il existe des phases spécifiques de l’exécution du programme durant lesquelles l’activité d’E/S de pagination est plus importante.

 Si vous collectez des données de profil pour une application ASP.NET dans un scénario de test de charge, essayez de réexécuter le test de charge sur un ordinateur configuré avec de la mémoire physique (ou RAM) supplémentaire.

 Envisagez de réduire les allocations de mémoire en modifiant les algorithmes et en évitant les API nécessitant beaucoup de mémoire, telles que String.Concat et String.Substring.
