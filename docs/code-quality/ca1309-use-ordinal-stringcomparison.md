---
title: 'CA1309 : Utiliser StringComparison avec la valeur Ordinal'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91953fd855576b6f40d02ebb3653fff07bfdef9c
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546429"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309 : Utiliser StringComparison avec la valeur Ordinal

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une opération de comparaison de chaînes qui est non linguistique ne définit pas le <xref:System.StringComparison> paramètre soit **Ordinal** ou **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Description de la règle
 Plusieurs opérations de chaîne, surtout la <xref:System.String.Compare%2A?displayProperty=fullName> et <xref:System.String.Equals%2A?displayProperty=fullName> méthodes, fournissent désormais une surcharge qui accepte un <xref:System.StringComparison?displayProperty=fullName> valeur d’énumération en tant que paramètre.

 Lorsque vous définissez **StringComparison.Ordinal** ou **StringComparison.OrdinalIgnoreCase**, la comparaison de chaînes est non linguistique. Autrement dit, les fonctionnalités qui sont spécifiques au langage naturel sont ignorées lors de décisions de comparaison. En ignorant les fonctionnalités de langage naturel signifie que les décisions reposent sur simples comparaisons d’octets et non sur la casse ou des tables d’équivalences paramétrables par la culture. Par conséquent, en affectant explicitement le paramètre soit le **StringComparison.Ordinal** ou **StringComparison.OrdinalIgnoreCase**, votre code souvent accélère, augmente l’exactitude et devient plus fiable.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la méthode de comparaison de chaînes à une surcharge qui accepte le <xref:System.StringComparison?displayProperty=fullName> énumération en tant que paramètre, puis spécifiez **Ordinal** ou **OrdinalIgnoreCase**. Par exemple, remplacez `String.Compare(str1, str2)` par `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle lorsque la bibliothèque ou l’application est destinée à une audience locale limitée, ou lorsque la sémantique de la culture actuelle doit être utilisée sans.

## <a name="see-also"></a>Voir aussi

- [Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)
- [CA1307 : Spécifiez StringComparison](../code-quality/ca1307-specify-stringcomparison.md)