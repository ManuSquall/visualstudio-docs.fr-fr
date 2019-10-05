---
title: "CA1031 : Ne pas intercepter des types d'exception générale"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c1dc1e5ed18ddcd42d42c96f3f853808c58ade48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236063"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031 : Ne pas intercepter des types d'exception générale

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une exception générale, telle <xref:System.Exception?displayProperty=fullName> que <xref:System.SystemException?displayProperty=fullName> ou, est interceptée dans une `catch` instruction, ou une clause catch `catch()` générale telle que est utilisée.

## <a name="rule-description"></a>Description de la règle
Les exceptions générales ne doivent pas être interceptées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, interceptez une exception plus spécifique ou levez à nouveau l’exception générale comme dernière instruction dans le `catch` bloc.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle. L’interception des types d’exception généraux peut masquer les problèmes d’exécution de l’utilisateur de la bibliothèque et peut rendre le débogage plus difficile.

> [!NOTE]
> À partir du .NET Framework 4, le Common Language Runtime (CLR) ne remet plus les exceptions d’état endommagé qui se produisent dans le système d’exploitation et le code managé, telles [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]que les violations d’accès dans, qui doivent être gérées par le code managé. Si vous souhaitez compiler une application dans le .NET Framework 4 ou versions ultérieures et maintenir la gestion des exceptions d’état endommagé, vous pouvez appliquer <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> l’attribut à la méthode qui gère l’exception d’état endommagé.

## <a name="example"></a>Exemple
L’exemple suivant montre un type qui enfreint cette règle et un type qui implémente correctement le `catch` bloc.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA2200 Lever à nouveau pour conserver les détails de la pile](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)