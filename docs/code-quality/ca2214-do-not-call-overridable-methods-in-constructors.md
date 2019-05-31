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
ms.openlocfilehash: 8e05e6925085b27de3001c8ff62d8a3c6e69a88f
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401311"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214 : N'appelez pas de méthodes substituables dans les constructeurs

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Le constructeur d’un type unsealed appelle une méthode virtuelle définie dans sa classe.

## <a name="rule-description"></a>Description de la règle

Lorsqu’une méthode virtuelle est appelée, le type réel qui exécute la méthode n’est pas sélectionné jusqu'à l’exécution. Lorsqu’un constructeur appelle une méthode virtuelle, il est possible que le constructeur pour l’instance qui appelle la méthode n’a pas été exécutée.

> [!NOTE]
> L’implémentation de l’analyse binaire de cette règle a un message de diagnostic différent de « **\[nom du constructeur] contient une chaîne d’appel qui entraîne un appel à une méthode virtuelle définie par la classe. Passez en revue la pile des appels suivants pour des conséquences inattendues**». Le [analyseurs FxCop](install-fxcop-analyzers.md) implémentation de cette règle a un message de diagnostic de «**n’appelez pas de méthodes substituables dans les constructeurs**».

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, n’appelez pas les méthodes virtuelles d’un type à partir de dans les constructeurs du type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Le constructeur doit être refondu pour éliminer l’appel à la méthode virtuelle.

## <a name="example"></a>Exemple

L’exemple suivant montre l’effet de violation de cette règle. L’application de test crée une instance de `DerivedType`, ce qui entraîne sa classe de base (`BadlyConstructedType`) constructeur à exécuter. `BadlyConstructedType`de manière incorrecte, le constructeur appelle la méthode virtuelle `DoSomething`. Comme le montre la sortie, `DerivedType.DoSomething()` s’exécute avant `DerivedType`du constructeur s’exécute.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Cet exemple génère la sortie suivante :

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```