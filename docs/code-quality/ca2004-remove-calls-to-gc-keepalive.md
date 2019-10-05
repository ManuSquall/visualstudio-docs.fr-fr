---
title: 'CA2004 : Supprimez les appels à GC.KeepAlive'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c495357b837c4ae10d4dfe1e25237d6caaefcc4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233111"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004 : Supprimez les appels à GC.KeepAlive

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Les classes `SafeHandle` utilisent mais contiennent toujours des `GC.KeepAlive`appels à.

## <a name="rule-description"></a>Description de la règle
Si vous effectuez une conversion `SafeHandle` vers l’utilisation, supprimez `GC.KeepAlive` tous les appels à (Object). Dans ce cas, les classes n’ont pas besoin `GC.KeepAlive`d’appeler, en supposant qu’elles n’ont pas de finaliseur, mais qu’elles s’appuient sur `SafeHandle` pour terminer le handle du système d’exploitation.  Bien que le coût de la sortie d’un `GC.KeepAlive` appel à puisse être négligeable comme mesuré par les performances, la perception `GC.KeepAlive` selon laquelle un appel à est nécessaire ou suffisant pour résoudre un problème de durée de vie qui n’existe peut-être plus rend le code plus difficile à maintenir.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Supprimez les `GC.KeepAlive`appels à.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Vous pouvez supprimer cet avertissement uniquement s’il n’est pas techniquement correct de le `SafeHandle` convertir en utilisation dans votre classe.