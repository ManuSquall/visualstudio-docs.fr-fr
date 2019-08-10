---
title: 'CA1309 : Utiliser StringComparison avec la valeur Ordinal'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c528266c54bbb2f3f0d9420461d700a46b09bd5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922284"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309 : Utiliser StringComparison avec la valeur Ordinal

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Catégorie|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une opération de comparaison de chaînes non linguistique ne définit pas le <xref:System.StringComparison> paramètre sur **ordinal** ou **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Description de la règle
De nombreuses opérations de chaînes, surtout les <xref:System.String.Compare%2A?displayProperty=fullName> méthodes <xref:System.String.Equals%2A?displayProperty=fullName> et, fournissent désormais une surcharge qui accepte une <xref:System.StringComparison?displayProperty=fullName> valeur d’énumération en tant que paramètre.

Lorsque vous spécifiez **StringComparison. Ordinal** ou **StringComparison. OrdinalIgnoreCase**, la comparaison de chaînes n’est pas linguistique. Autrement dit, les fonctionnalités spécifiques au langage naturel sont ignorées lorsque des décisions de comparaison sont prises. En ignorant les fonctionnalités de langage naturel, les décisions sont basées sur des comparaisons d’octets simples et non sur la casse ou des tables d’équivalences paramétrables par la culture. Par conséquent, en affectant explicitement au paramètre la valeur **StringComparison. Ordinal** ou **StringComparison. OrdinalIgnoreCase**, votre code gagne souvent en vitesse, augmente l’exactitude et devient plus fiable.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, remplacez la méthode de comparaison de chaînes par une surcharge qui <xref:System.StringComparison?displayProperty=fullName> accepte l’énumération en tant que paramètre et spécifiez **ordinal** ou **OrdinalIgnoreCase**. Par exemple, remplacez `String.Compare(str1, str2)` par `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle lorsque la bibliothèque ou l’application est destinée à un public local limité ou lorsque la sémantique de la culture actuelle doit être utilisée.

## <a name="see-also"></a>Voir aussi

- [Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)
- [CA1307 Spécifier StringComparison](../code-quality/ca1307-specify-stringcomparison.md)