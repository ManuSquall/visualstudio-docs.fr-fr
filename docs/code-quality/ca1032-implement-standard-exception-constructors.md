---
title: "CA1032 : Implémenter des constructeurs d'exception standard"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06fdc566abd9bd16758f224f8a9fe805cddb2c61
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236046"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032 : Implémenter des constructeurs d'exception standard

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type étend <xref:System.Exception?displayProperty=fullName> mais ne déclare pas tous les constructeurs requis.

## <a name="rule-description"></a>Description de la règle

Les types d’exceptions doivent implémenter les trois constructeurs suivants :

- public NewException ()

- public NewException (String)

- public NewException (String, exception)

En outre, si vous exécutez l’analyse FxCop héritée par opposition à [des analyseurs FxCop basés sur .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md), l’absence d’un quatrième constructeur génère également une violation :

- NewException protected ou Private (SerializationInfo, StreamingContext)

Ne pas fournir le jeu complet de constructeurs peut rendre difficile une gestion des exceptions correcte. Par exemple, le constructeur qui possède la signature `NewException(string, Exception)` est utilisé pour créer des exceptions provoquées par d’autres exceptions. Sans ce constructeur, vous ne pouvez pas créer et lever une instance de votre exception personnalisée qui contient une exception interne (imbriquée), ce que le code managé doit faire dans une telle situation.

Les trois premiers constructeurs d’exception sont publics par Convention. Le quatrième constructeur est protégé dans les classes non scellées et privé dans les classes sealed. Pour plus d’informations, [consultez CA2229 : Implémentez des constructeurs](../code-quality/ca2229-implement-serialization-constructors.md)de sérialisation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, ajoutez les constructeurs manquants à l’exception et assurez-vous qu’ils ont l’accessibilité correcte.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle lorsque la violation est provoquée par l’utilisation d’un niveau d’accès différent pour les constructeurs publics. En outre, il est possible de supprimer l’avertissement pour le `NewException(SerializationInfo, StreamingContext)` constructeur si vous générez une bibliothèque de classes portables (PCL).

## <a name="example"></a>Exemple

L’exemple suivant contient un type d’exception qui enfreint cette règle et un type d’exception qui est correctement implémenté.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Voir aussi

[CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)