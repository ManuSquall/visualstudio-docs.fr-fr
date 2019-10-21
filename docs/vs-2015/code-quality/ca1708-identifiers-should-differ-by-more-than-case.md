---
title: 'CA1708 : les identificateurs ne doivent pas différer uniquement par leur casse | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f611cb899a2386c47e1370214a74c2a5da52584f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669200"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708 : Les identificateurs ne doivent pas différer que par leur casse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Les noms de deux types, membres, paramètres ou espaces de noms qualifiés complets sont identiques lorsqu’ils sont convertis en minuscules.

## <a name="rule-description"></a>Description de la règle
 Les identificateurs des espaces de noms, types, membres et paramètres ne peuvent pas différer uniquement par la casse car les langages qui ciblent le Common Language Runtime ne sont pas tenus de respecter celle-ci. Par exemple, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] est un langage non sensible à la casse largement utilisé.

 Cette règle se déclenche uniquement sur les membres visibles publiquement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Sélectionnez un nom unique lorsqu’il est comparé à d’autres identificateurs sans respect de la casse.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. La bibliothèque n’est peut-être pas utilisable dans toutes les langues disponibles dans le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="example-of-a-violation"></a>Exemple de violation
 L’exemple suivant illustre une violation de cette règle.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
