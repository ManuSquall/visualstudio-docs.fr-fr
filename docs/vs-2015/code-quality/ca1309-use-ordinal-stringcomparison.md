---
title: 'CA1309 : Utiliser StringComparison avec la valeur ordinale | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d244c51d06993d482cb3c8f70834c033bae3f74a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200406"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309 : Utiliser StringComparison avec la valeur Ordinal
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une opération de comparaison de chaînes qui est non linguistique ne définit pas le <xref:System.StringComparison> paramètre soit **Ordinal** ou **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Description de la règle
 Plusieurs opérations de chaîne, plus importantes la <xref:System.String.Compare%2A?displayProperty=fullName> et <xref:System.String.Equals%2A?displayProperty=fullName> méthodes, fournissent désormais une surcharge qui accepte un <xref:System.StringComparison?displayProperty=fullName> valeur d’énumération en tant que paramètre.

 Lorsque vous définissez **StringComparison.Ordinal** ou **StringComparison.OrdinalIgnoreCase**, la comparaison de chaînes est non linguistique. Autrement dit, les fonctionnalités qui sont spécifiques au langage naturel sont ignorées lors de décisions de comparaison. Cela signifie que les décisions reposent sur simples comparaisons d’octets et ignorent la casse ou équivalence des tables qui sont paramétrables par la culture. Par conséquent, en affectant explicitement le paramètre soit le **StringComparison.Ordinal** ou **StringComparison.OrdinalIgnoreCase**, votre code souvent accélère, augmente l’exactitude et devient plus fiable.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la méthode de comparaison de chaînes à une surcharge qui accepte le <xref:System.StringComparison?displayProperty=fullName> énumération en tant que paramètre, puis spécifiez **Ordinal** ou **OrdinalIgnoreCase**. Par exemple, remplacez `String.Compare(str1, str2)` par `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle lorsque la bibliothèque ou l’application est destiné à une audience locale limitée ou lorsque la sémantique de la culture actuelle doit être utilisée sans.

## <a name="see-also"></a>Voir aussi
 [Avertissements de globalisation](../code-quality/globalization-warnings.md) [CA1307 : spécifier StringComparison](../code-quality/ca1307-specify-stringcomparison.md)



