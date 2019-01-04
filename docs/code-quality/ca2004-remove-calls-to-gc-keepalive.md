---
title: 'CA2004 : Supprimez les appels à GC. KeepAlive'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e025a8af3f7f5c1810abe2b9e182f607a29760e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915829"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004 : Supprimez les appels à GC. KeepAlive

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Classes utilisent `SafeHandle` mais contiennent toujours des appels à `GC.KeepAlive`.

## <a name="rule-description"></a>Description de la règle
 Si vous convertissez en `SafeHandle` utilisation, supprimez tous les appels à `GC.KeepAlive` (objet). Dans ce cas, les classes ne requièrent pas d’appeler `GC.KeepAlive`, en supposant qu’elles n’ont pas de finaliseur, mais dépendent `SafeHandle` pour terminer le handle du système d’exploitation pour eux.  Bien que le coût de laisser dans un appel à `GC.KeepAlive` peut être négligeable en termes de performances, la perception qui un appel à `GC.KeepAlive` est nécessaire ou suffit à résoudre le problème qui ne peut plus exister rend le code plus difficile pour une durée de vie mettre à jour.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez les appels à `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous pouvez supprimer cet avertissement uniquement si elle n’est pas techniquement correcte convertir `SafeHandle` utilisation dans votre classe.