---
title: 'CA1307 : spécifier StringComparison | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 033d8f0e22ec040ffb10821993a5a9c647ee401e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538916"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307 : Spécifier StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de <xref:System.StringComparison> paramètre.

## <a name="rule-description"></a>Description de la règle
 De nombreuses opérations de chaînes, dont les plus importantes <xref:System.String.Compare%2A> <xref:System.String.Equals%2A> sont les méthodes et, fournissent une surcharge qui accepte une <xref:System.StringComparison> valeur d’énumération en tant que paramètre.

 Lorsqu’il existe une surcharge qui accepte un <xref:System.StringComparison> paramètre, elle doit être utilisée à la place d’une surcharge qui n’accepte pas ce paramètre. En définissant ce paramètre de manière explicite, votre code est souvent plus clair et plus facile à gérer.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez les méthodes de comparaison de chaînes par des surcharges qui acceptent l' <xref:System.StringComparison> énumération en tant que paramètre. Par exemple : remplacez `String.Compare(str1, str2)` par `String.Compare(str1, str2, StringComparison.Ordinal)` .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque la bibliothèque ou l’application est destinée à un public local limité et ne sera donc pas localisée.

## <a name="see-also"></a>Voir aussi
 [Avertissements de globalisation](../code-quality/globalization-warnings.md) [Ca1309 : utiliser la StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)
