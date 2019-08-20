---
title: 'CA1307 : Spécifier StringComparison | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 292e174feeb123c640306bc8ef3ffedd7e8847f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200349"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307 : Spécifier StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Catégorie|Microsoft.Globalization|
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
 [Avertissements de globalisation](../code-quality/globalization-warnings.md) [CA1309 : Utiliser StringComparison avec la valeur ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)
