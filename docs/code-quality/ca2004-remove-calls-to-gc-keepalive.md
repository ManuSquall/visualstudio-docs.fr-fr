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
ms.openlocfilehash: a716da8eb0fb1b741c302ed32408e63a4933567b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921139"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004 : Supprimez les appels à GC.KeepAlive

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Catégorie|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Les classes `SafeHandle` utilisent mais contiennent toujours des `GC.KeepAlive`appels à.

## <a name="rule-description"></a>Description de la règle
Si vous effectuez une conversion `SafeHandle` vers l’utilisation, supprimez `GC.KeepAlive` tous les appels à (Object). Dans ce cas, les classes n’ont pas besoin `GC.KeepAlive`d’appeler, en supposant qu’elles n’ont pas de finaliseur, mais qu’elles s’appuient sur `SafeHandle` pour terminer le handle du système d’exploitation.  Bien que le coût de la sortie d’un `GC.KeepAlive` appel à puisse être négligeable comme mesuré par les performances, la perception `GC.KeepAlive` selon laquelle un appel à est nécessaire ou suffisant pour résoudre un problème de durée de vie qui n’existe peut-être plus rend le code plus difficile à maintenir.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Supprimez les `GC.KeepAlive`appels à.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Vous pouvez supprimer cet avertissement uniquement s’il n’est pas techniquement correct de le `SafeHandle` convertir en utilisation dans votre classe.