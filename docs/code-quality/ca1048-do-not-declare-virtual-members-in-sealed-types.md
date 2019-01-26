---
title: 'CA1048 : Ne pas déclarer les membres virtuels dans les types sealed'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 531590eee7804debfc8ccfb9a8e508107fba71df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006726"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048 : Ne pas déclarer les membres virtuels dans les types sealed

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public est sealed et déclare une méthode qui est à la fois `virtual` (`Overridable` en Visual Basic) et non finale. Cette règle ne signale pas de violations pour les types délégués, qui doivent respecter ce modèle.

## <a name="rule-description"></a>Description de la règle
 Les types déclarent des méthodes comme étant virtuelles afin d'hériter de types en mesure de substituer l'implémentation de la méthode virtuelle. Par définition, vous ne peut pas hériter d’un type sealed, effectuer une méthode virtuelle sur un type sealed sans signification.

 Les compilateurs c# et Visual Basic n’autorisent pas les types de violer cette règle.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez la méthode non virtuelle ou rendez le type pouvant être héritées.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Laisser le type dans son état actuel peut entraîner des problèmes de maintenance et ne fournit pas d’avantages.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type qui enfreint cette règle.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]