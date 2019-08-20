---
title: 'CA1047 : Ne pas déclarer les membres protégés dans les types sealed'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5ab7cf2c5a4f17966ed5b4da30657e05a4683738
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922649"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047 : Ne pas déclarer les membres protégés dans les types sealed

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type public est `sealed` (`NotInheritable` en Visual Basic) et déclare un membre protégé ou un type imbriqué protégé. Cette règle ne signale pas de <xref:System.Object.Finalize%2A> violations pour les méthodes, qui doivent suivre ce modèle.

## <a name="rule-description"></a>Description de la règle
Les types déclarent des membres protégés afin que des types qui héritent puissent accéder au membre ou le substituer. Par définition, vous ne pouvez pas hériter d’un type sealed, ce qui signifie que les méthodes protégées sur les types sealed ne peuvent pas être appelées.

Le C# compilateur émet un avertissement pour cette erreur.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, modifiez le niveau d’accès du membre en privé ou rendez le type héritable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle. Le fait de laisser le type dans son état actuel peut entraîner des problèmes de maintenance et ne fournit aucun avantage.

## <a name="example"></a>Exemple
L’exemple suivant montre un type qui viole cette règle.

[!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
[!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]