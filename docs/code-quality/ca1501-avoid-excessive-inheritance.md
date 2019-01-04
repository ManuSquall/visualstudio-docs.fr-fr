---
title: 'CA1501 : Éviter l’excès d’héritage'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 030d1d520ef2feb1f7b530c55c609a1cd951893b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861067"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501 : Éviter l’excès d’héritage

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Category|Microsoft.Maintainability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage.

## <a name="rule-description"></a>Description de la règle
 Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer. Cette règle limite l’analyse aux hiérarchies dans le même module.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, dérivez le type d’un type de base moins imbriqué dans la hiérarchie d’héritage ou éliminer certains des types de base intermédiaires.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle. Toutefois, le code peut être plus difficile à gérer. Notez que, en fonction de la visibilité des types de base, résolution des violations de cette règle peut créer des modifications avec rupture. Par exemple, la suppression des types de base publiques est une modification avec rupture.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle.

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]