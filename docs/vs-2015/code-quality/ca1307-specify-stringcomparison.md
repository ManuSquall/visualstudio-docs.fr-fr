---
title: 'CA1307 : Spécifier StringComparison | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 2c96b8c895106337a8578b6662c0e61830b38f55
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589993"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307 : Spécifier StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1307 : spécifier StringComparison avec la valeur](https://docs.microsoft.com/visualstudio/code-quality/ca1307-specify-stringcomparison).

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
 [Avertissements de globalisation](../code-quality/globalization-warnings.md) [CA1309 : utiliser StringComparison avec la valeur ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)



