---
title: 'CA1307 : Spécifier StringComparison'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce2da2c1ff5b2f74d8b4d6341050c1895b68955a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922291"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307 : Spécifier StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Catégorie|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne <xref:System.StringComparison> définit pas de paramètre.

## <a name="rule-description"></a>Description de la règle
De nombreuses opérations de chaînes, dont <xref:System.String.Compare%2A> les <xref:System.String.Equals%2A> plus importantes sont les méthodes et, fournissent <xref:System.StringComparison> une surcharge qui accepte une valeur d’énumération en tant que paramètre.

Lorsqu’il existe une surcharge qui accepte <xref:System.StringComparison> un paramètre, elle doit être utilisée à la place d’une surcharge qui n’accepte pas ce paramètre. En définissant ce paramètre de manière explicite, votre code est souvent plus clair et plus facile à gérer.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, remplacez les méthodes de comparaison de chaînes par des surcharges qui acceptent l' <xref:System.StringComparison> énumération en tant que paramètre. Par exemple: remplacez `String.Compare(str1, str2)` `String.Compare(str1, str2, StringComparison.Ordinal)`par.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle lorsque la bibliothèque ou l’application est destinée à un public local limité et ne sera donc pas localisée.

## <a name="see-also"></a>Voir aussi

- [Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)
- [CA1309 Utiliser StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)