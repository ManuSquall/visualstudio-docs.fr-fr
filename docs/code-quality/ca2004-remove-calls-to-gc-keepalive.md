---
title: 'CA2004 : Supprimez les appels à GC.KeepAlive'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: fa59c6797d81202637f44799327e6b2802d822eb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004 : Supprimez les appels à GC.KeepAlive
|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Utilisation des classes `SafeHandle` mais contiennent toujours des appels à `GC.KeepAlive`.

## <a name="rule-description"></a>Description de la règle
 Si vous convertissez en `SafeHandle` utilisation, supprimez tous les appels à `GC.KeepAlive` (objet). Dans ce cas, les classes devez pas appeler `GC.KeepAlive`, en supposant qu’elles n’ont pas de finaliseur mais dépendent `SafeHandle` pour terminer le handle du système d’exploitation pour eux.  Bien que le coût de laisser dans un appel à `GC.KeepAlive` peut être négligeable en termes de performances, la perception qui un appel à `GC.KeepAlive` est nécessaire ou suffisant pour résoudre le problème qui ne peut plus exister rend le code plus difficile pour une durée de vie mettre à jour.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez les appels à `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous pouvez supprimer cet avertissement uniquement si elle n’est pas techniquement correcte convertir `SafeHandle` utilisation dans votre classe.