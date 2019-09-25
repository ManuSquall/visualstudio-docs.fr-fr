---
title: "CA2208 : Instanciez les exceptions d'argument comme il se doit"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9f9425ab1ea9eadd3bd06d950118ce83ba5c35f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231642"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208 : Instanciez les exceptions d'argument comme il se doit

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Les causes possibles sont les suivantes :

- Un appel est passé au constructeur par défaut (sans paramètre) d’un type d’exception qui est ou dérive de <xref:System.ArgumentException>.

- Un argument de chaîne incorrect est passé à un constructeur paramétrable d’un type d’exception qui est ou dérive <xref:System.ArgumentException>de.

## <a name="rule-description"></a>Description de la règle

Au lieu d’appeler le constructeur par défaut, appelez l’une des surcharges de constructeur qui permet de fournir un message d’exception plus explicite. Le message d’exception doit cibler le développeur et expliquer clairement la condition d’erreur et comment corriger ou éviter l’exception.

Les signatures des constructeurs de chaîne un et deux de et <xref:System.ArgumentException> de ses types dérivés ne sont pas cohérentes par rapport `message` à `paramName` la position et aux paramètres. Assurez-vous que ces constructeurs sont appelés avec les arguments de chaîne corrects. Les signatures sont les suivantes :

- <xref:System.ArgumentException>(chaîne `message`)
- <xref:System.ArgumentException>(String `message`, String `paramName`)
- <xref:System.ArgumentNullException>(chaîne `paramName`)
- <xref:System.ArgumentNullException>(String `paramName`, String `message`)
- <xref:System.ArgumentOutOfRangeException>(chaîne `paramName`)
- <xref:System.ArgumentOutOfRangeException>(String `paramName`, String `message`)
- <xref:System.DuplicateWaitObjectException>(chaîne `parameterName`)
- <xref:System.DuplicateWaitObjectException>(String `parameterName`, String `message`)

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appelez un constructeur qui accepte un message, un nom de paramètre, ou les deux, et assurez-vous que les arguments sont <xref:System.ArgumentException> corrects pour le type d’appel.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle uniquement si un constructeur paramétré est appelé avec les arguments de chaîne appropriés.

## <a name="example"></a>Exemple

Le code suivant illustre un constructeur qui instancie de manière incorrecte une <xref:System.ArgumentNullException>instance de.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

Le code suivant résout la violation précédente en basculant les arguments du constructeur.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Règles associées

- [CA1507 : Utiliser nameof à la place de String](ca1507.md)