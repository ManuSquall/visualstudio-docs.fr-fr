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
ms.openlocfilehash: e3b3d979910883f6be9f542ec581ecbda0f91deb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444373"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307 : Spécifier StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre <xref:System.StringComparison>.

## <a name="rule-description"></a>Description de la règle
De nombreuses opérations de chaînes, plus importantes les méthodes <xref:System.String.Compare%2A> et <xref:System.String.Equals%2A>, fournissent une surcharge qui accepte une valeur d’énumération <xref:System.StringComparison> comme paramètre.

Lorsqu’il existe une surcharge qui accepte un paramètre <xref:System.StringComparison>, elle doit être utilisée à la place d’une surcharge qui n’accepte pas ce paramètre. En définissant ce paramètre de manière explicite, votre code est souvent plus clair et plus facile à gérer.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, remplacez les méthodes de comparaison de chaînes par des surcharges qui acceptent l’énumération <xref:System.StringComparison> en tant que paramètre. Par exemple : remplacez `String.Compare(str1, str2)` par `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle lorsque la bibliothèque ou l’application est destinée à un public local limité et ne sera donc pas localisée.

## <a name="see-also"></a>Voir aussi

- [Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)
- [CA1309 : Utilisez StringComparison avec la valeur Ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)
