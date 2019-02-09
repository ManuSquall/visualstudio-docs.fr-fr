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
ms.openlocfilehash: a3aabd73a3c234be61cecdf68fbc92fc7e52883e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927683"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307 : Spécifier StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas un <xref:System.StringComparison> paramètre.

## <a name="rule-description"></a>Description de la règle
 Plusieurs opérations de chaîne, plus importantes la <xref:System.String.Compare%2A> et <xref:System.String.Equals%2A> méthodes, fournissent une surcharge qui accepte un <xref:System.StringComparison> valeur d’énumération en tant que paramètre.

 Chaque fois que les existe une surcharge qui accepte un <xref:System.StringComparison> paramètre, il doit être utilisé au lieu d’une surcharge qui n’accepte pas ce paramètre. En affectant explicitement à ce paramètre, votre code est souvent plus clair et plus facile à gérer.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifier les méthodes de comparaison de chaînes pour les surcharges qui acceptent le <xref:System.StringComparison> énumération en tant que paramètre. Par exemple : modifier `String.Compare(str1, str2)` à `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle lorsque la bibliothèque ou l’application est destinée à une audience locale limitée et ne sera donc pas traduite.

## <a name="see-also"></a>Voir aussi

- [Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)
- [CA1309 : Utiliser StringComparison avec la valeur ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)