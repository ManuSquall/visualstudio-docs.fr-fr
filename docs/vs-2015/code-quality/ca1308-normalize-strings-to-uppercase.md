---
title: 'CA1308 : Normaliser les chaînes en majuscules | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8385839ce7029ef0676225fd443582ba750b618b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200383"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308 : Normaliser les chaînes en majuscules
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Catégorie|Microsoft.Globalization|
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
