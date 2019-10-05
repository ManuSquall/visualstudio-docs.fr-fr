---
title: 'CA1719 : Les noms des paramètres ne doivent pas être identiques aux noms des membres'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2aa55993758df24346b78eb4d9ad022014d9d81c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233986"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719 : Les noms des paramètres ne doivent pas être identiques aux noms des membres

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Le nom d’un membre visible de l’extérieur correspond, dans une comparaison qui ne respecte pas la casse, au nom de l’un de ses paramètres.

## <a name="rule-description"></a>Description de la règle
Un nom de paramètre doit véhiculer la signification du paramètre et un nom de membre celle du membre. Un design où ceux-ci sont identiques est rare. Donner à un paramètre le même que son membre n'est pas une méthode intuitive et rend la bibliothèque difficile à utiliser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Sélectionnez un nom de paramètre qui ne correspond pas au nom du membre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Pour un nouveau développement, aucun scénario connu ne se produit lorsque vous devez supprimer un avertissement de cette règle. Pour les bibliothèques d’expédition, vous devrez peut-être supprimer un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
[CA1709 La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

[CA1708 Les identificateurs ne doivent pas différer uniquement par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

[CA1707 Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)