---
title: 'CA1053 : Les types de conteneurs statiques ne doivent pas comporter de constructeur'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44bdb8c12b48a983b88e6a035fc1522856b306be
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235584"
---
# <a name="ca1053-static-holder-types-should-not-have-default-constructors"></a>CA1053 : Les types de conteneurs statiques ne doivent pas avoir de constructeurs par défaut

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

> [!NOTE]
> La règle ca1053 est combinée [dans CA1052 : Les types de conteneurs statiques](ca1052-static-holder-types-should-be-sealed.md) doivent être scellés dans les [analyseurs FxCop](fxcop-analyzers.yml).

## <a name="cause"></a>Cause

Un type public ou imbriqué ne déclare que des membres statiques et a un constructeur par défaut.

## <a name="rule-description"></a>Description de la règle

Le constructeur par défaut n’est pas nécessaire, car l’appel de membres statiques ne requiert pas une instance du type. En outre, étant donné que le type n’a pas de membres non statiques, la création d’une instance ne permet pas d’accéder aux membres du type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le constructeur par défaut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. La présence du constructeur par défaut suggère que le type n’est pas un type static.