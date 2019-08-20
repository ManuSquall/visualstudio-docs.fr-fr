---
title: 'CA1308 : Normaliser les chaînes en majuscules'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06fe8d4fbd4def14bfb8a24f4f211a121c809930
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922242"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308 : Normaliser les chaînes en majuscules

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Catégorie|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une opération normalise une chaîne en minuscules.

## <a name="rule-description"></a>Description de la règle
Les chaînes doivent être normalisées en majuscules. Un petit groupe de caractères, lorsqu’ils sont convertis en minuscules, ne peut pas faire l’objet d’un aller-retour. Pour effectuer un aller-retour, vous pouvez convertir les caractères d’un paramètre régional en un autre paramètre régional qui représente les données de caractères différemment, puis récupérer avec précision les caractères d’origine à partir des caractères convertis.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Les opérations de modification qui convertissent les chaînes en minuscules afin que les chaînes soient converties en majuscules. Par exemple, remplacez `String.ToLower(CultureInfo.InvariantCulture)` par `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un message d’avertissement lorsque vous ne faites pas de décision de sécurité basée sur le résultat (par exemple, quand vous l’affichez dans l’interface utilisateur).

## <a name="see-also"></a>Voir aussi
[Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)