---
title: 'CA2132 : Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c5ca98219444515d01baf670489120238cb8dda
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232336"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132 : Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

> [!NOTE]
> Cet avertissement est appliqué uniquement au code qui exécute CoreCLR (la version du CLR qui est spécifique aux applications Web Silverlight).

## <a name="cause"></a>Cause

L’attribut Transparency du constructeur par défaut d’une classe dérivée n’est pas aussi critique que la transparence de la classe de base.

## <a name="rule-description"></a>Description de la règle

Les types et les membres qui <xref:System.Security.SecurityCriticalAttribute> ont le ne peuvent pas être utilisés par le code d’application Silverlight. Les types et membres critiques de sécurité (security-critical) peuvent être uniquement utilisés par le code de confiance dans la bibliothèque de classes .NET Framework pour Silverlight. Dans la mesure où une construction publique ou protégée dans une classe dérivée doit avoir la même transparence ou une transparence supérieure à sa classe de base, une classe dans une application ne peut pas être dérivée d’une classe marquée SecurityCritical.

Pour le code de plateforme CoreCLR, si un type de base a un constructeur par défaut non transparent public ou protégé, le type dérivé doit respecter les règles d’héritage du constructeur par défaut. Le type dérivé doit également avoir un constructeur par défaut et ce constructeur doit être au moins comme constructeur par défaut critique du type de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger la violation, supprimez le type ou ne dérivez pas de type non transparent de sécurité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas les avertissements de cette règle. Les violations de cette règle par le code d’application entraînent le refus de CoreCLR de charger le type <xref:System.TypeLoadException>avec un.

### <a name="code"></a>Code

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]