---
title: 'CA1308 : Normaliser les chaînes en majuscules'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 87a672737f3c5d7287215bdd4930e25fb2981825
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924216"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308 : Normaliser les chaînes en majuscules

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une opération normalise une chaîne en minuscules.

## <a name="rule-description"></a>Description de la règle
 Les chaînes doivent être normalisées en majuscules. Un petit groupe de caractères, lorsqu’ils sont convertis en minuscules, ne peut pas faire un aller-retour. Pour faire un aller-retour signifie convertir les caractères à partir des paramètres régionaux pour les autres paramètres régionaux qui représente des données caractères différemment, puis à précisément récupérer les caractères d’origine à partir des caractères convertis.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Modifiez les opérations qui convertissent des chaînes en minuscules afin que les chaînes sont converties en majuscules à la place. Par exemple, remplacez `String.ToLower(CultureInfo.InvariantCulture)` par `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un message d’avertissement lorsque vous n’effectuez pas de décision de sécurité en fonction du résultat (par exemple, lorsque vous l’affichez dans l’interface utilisateur) sans.

## <a name="see-also"></a>Voir aussi
 [Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)