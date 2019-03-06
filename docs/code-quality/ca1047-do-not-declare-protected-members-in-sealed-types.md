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
ms.openlocfilehash: c138c05d755b05275755f96776764604997cbbcd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921547"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047 : Ne pas déclarer les membres protégés dans les types sealed

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Est un type public `sealed` (`NotInheritable` en Visual basic) et déclare un membre protégé ou un type imbriqué protégé. Cette règle ne signale pas de violations pour <xref:System.Object.Finalize%2A> méthodes, qui doivent respecter ce modèle.

## <a name="rule-description"></a>Description de la règle
 Les types déclarent des membres protégés afin que des types qui héritent puissent accéder au membre ou le substituer. Par définition, vous ne peut pas hériter d’un type sealed, ce qui signifie que protégés des méthodes sur les types sealed ne peut pas être appelée.

 Le compilateur c# émet un avertissement pour cette erreur.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifier le niveau d’accès du membre privé ou rendez le type héritable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Laisser le type dans son état actuel peut entraîner des problèmes de maintenance et ne fournit pas d’avantages.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type qui enfreint cette règle.

 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]