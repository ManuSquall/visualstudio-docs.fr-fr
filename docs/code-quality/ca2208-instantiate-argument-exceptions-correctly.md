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
ms.openlocfilehash: 2110a8d0b58d87a4554971cf00af6441d293aa91
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975886"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208 : Instanciez les exceptions d'argument comme il se doit

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Les causes possibles incluent les situations suivantes :

- Un appel est effectué au constructeur par défaut (sans paramètre) d’un type d’exception qui est ou dérive, <xref:System.ArgumentException>.

- Un argument string incorrect est passé à un constructeur paramétrable d’un type d’exception qui est ou dérive, <xref:System.ArgumentException>.

## <a name="rule-description"></a>Description de la règle

Au lieu d’appeler le constructeur par défaut, appelez une des surcharges de constructeur qui permet à un message d’exception plus explicite doit être fourni. Le message d’exception doit cibler le développeur et expliquer clairement la condition d’erreur et comment corriger ou éviter l’exception.

Les signatures des constructeurs de chaîne un et deux de <xref:System.ArgumentException> et ses types dérivés ne sont pas cohérents par rapport à la position `message` et `paramName` paramètres. Assurez-vous que ces constructeurs sont appelés avec les arguments de chaîne correcte. Les signatures sont les suivantes :

- <xref:System.ArgumentException>(chaîne `message`)
- <xref:System.ArgumentException>(chaîne `message`, chaîne `paramName`)
- <xref:System.ArgumentNullException>(chaîne `paramName`)
- <xref:System.ArgumentNullException>(chaîne `paramName`, chaîne `message`)
- <xref:System.ArgumentOutOfRangeException>(chaîne `paramName`)
- <xref:System.ArgumentOutOfRangeException>(chaîne `paramName`, chaîne `message`)
- <xref:System.DuplicateWaitObjectException>(chaîne `parameterName`)
- <xref:System.DuplicateWaitObjectException>(chaîne `parameterName`, chaîne `message`)

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appelez un constructeur qui accepte un message, un nom de paramètre ou les deux et assurez-vous que les arguments sont appropriées pour le type de <xref:System.ArgumentException> qui est appelée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle uniquement si un constructeur paramétrable est appelé avec les arguments de chaîne correcte.

## <a name="example"></a>Exemple

Le code suivant illustre un constructeur qui n’instancie pas correctement une instance de <xref:System.ArgumentNullException>.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

Le code suivant corrige la violation précédente en passant les arguments de constructeur.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Règles associées

- [CA1507 : Utilisez nameof à la place de chaîne](ca1507.md)