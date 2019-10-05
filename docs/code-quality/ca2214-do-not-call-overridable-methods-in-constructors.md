---
title: "CA2214 : N'appelez pas de méthodes substituables dans les constructeurs"
ms.date: 05/29/2016
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8eb881da0a7ed243bda35079f617a314053f2d85
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231287"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214 : N'appelez pas de méthodes substituables dans les constructeurs

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Le constructeur d’un type non scellé appelle une méthode virtuelle définie dans sa classe.

## <a name="rule-description"></a>Description de la règle

Quand une méthode virtuelle est appelée, le type réel qui exécute la méthode n’est pas sélectionné jusqu’au moment de l’exécution. Quand un constructeur appelle une méthode virtuelle, il est possible que le constructeur de l’instance qui appelle la méthode n’ait pas été exécuté.

> [!NOTE]
> L’implémentation d’analyse héritée de cette règle a un message de diagnostic**différent de « nom du constructeur »\[contient une chaîne d’appel qui entraîne un appel à une méthode virtuelle définie par la classe. Passez en revue la pile d’appels suivante pour**les conséquences inattendues». L’implémentation des [analyseurs FxCop](install-fxcop-analyzers.md) de cette règle a un message de diagnostic «**ne pas appeler les méthodes substituables dans les constructeurs**».

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, n’appelez pas les méthodes virtuelles d’un type à partir des constructeurs du type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Le constructeur doit être repensé pour éliminer l’appel à la méthode virtuelle.

## <a name="example"></a>Exemple

L’exemple suivant illustre l’effet de la violation de cette règle. L’application de test crée une instance `DerivedType`de, ce qui entraîne l’exécution`BadlyConstructedType`du constructeur de la classe de base (). `BadlyConstructedType`le constructeur de n’appelle pas correctement la méthode `DoSomething`virtuelle. Comme le montre la sortie `DerivedType.DoSomething()` , s’exécute `DerivedType`avant l’exécution du constructeur de.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Cet exemple génère la sortie suivante :

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```