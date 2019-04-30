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
ms.openlocfilehash: d82b1884336b314e8fcede3c6041030a878b999c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806762"
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

- Un appel est effectué au constructeur par défaut (sans paramètre) d’un type d’exception qui est ou dérive <xref:System.ArgumentException>.

- Un argument string incorrect est passé à un constructeur paramétrable d’un type d’exception qui est ou dérive <xref:System.ArgumentException>.

## <a name="rule-description"></a>Description de la règle

Au lieu d’appeler le constructeur par défaut, appelez une des surcharges de constructeur qui permet à un message d’exception plus explicite doit être fourni. Le message d’exception doit cibler le développeur et expliquer clairement la condition d’erreur et comment corriger ou éviter l’exception.

Les signatures des constructeurs de chaîne un et deux de <xref:System.ArgumentException> et ses types dérivés ne sont pas cohérents par rapport à la `message` et `paramName` paramètres. Assurez-vous que ces constructeurs sont appelés avec les arguments de chaîne correcte. Les signatures sont les suivantes :

 <xref:System.ArgumentException>(chaîne `message`)

 <xref:System.ArgumentException>(chaîne `message`, chaîne `paramName`)

 <xref:System.ArgumentNullException>(chaîne `paramName`)

 <xref:System.ArgumentNullException>(chaîne `paramName`, chaîne `message`)

 <xref:System.ArgumentOutOfRangeException>(chaîne `paramName`)

 <xref:System.ArgumentOutOfRangeException>(chaîne `paramName`, chaîne `message`)

 <xref:System.DuplicateWaitObjectException>(chaîne `parameterName`)

 <xref:System.DuplicateWaitObjectException>(chaîne `parameterName`, chaîne `message`)

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez un constructeur qui accepte un message, un nom de paramètre ou les deux et assurez-vous que les arguments sont appropriées pour le type de <xref:System.ArgumentException> qui est appelée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle uniquement si un constructeur paramétrable est appelé avec les arguments de chaîne correcte.

## <a name="example-1"></a>Exemple 1
 L’exemple suivant montre un constructeur qui n’instancie pas correctement une instance du type ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example-2"></a>Exemple 2
 L’exemple suivant résout la violation ci-dessus en passant les arguments de constructeur.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]