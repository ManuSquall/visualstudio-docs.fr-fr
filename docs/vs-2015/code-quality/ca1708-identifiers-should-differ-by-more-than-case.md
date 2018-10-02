---
title: 'CA1708 : Les identificateurs doivent différer par leur casse | Microsoft Docs'
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
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d60c29b7e6a5cec32b8a694bb0b21d7f85538e01
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590251"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708 : Les identificateurs ne doivent pas différer que par leur casse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1708 : les identificateurs doivent différer par leur casse](https://docs.microsoft.com/visualstudio/code-quality/ca1708-identifiers-should-differ-by-more-than-case).

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Les noms des deux types, membres, paramètres ou des espaces de noms qualifiés complets sont identiques lorsqu’ils sont convertis en minuscules.

## <a name="rule-description"></a>Description de la règle
 Les identificateurs des espaces de noms, types, membres et paramètres ne peuvent pas différer uniquement par la casse car les langages qui ciblent le Common Language Runtime ne sont pas tenus de respecter celle-ci. Par exemple, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] est un langage de non-respect de la casse largement utilisé.

 Cette règle se déclenche sur uniquement les membres visibles publiquement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Sélectionnez un nom qui est unique lorsqu’elle est comparée à d’autres identificateurs dans la casse.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. La bibliothèque ne peut pas être utilisable dans toutes les langues disponibles dans le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="example-of-a-violation"></a>Exemple de Violation
 L’exemple suivant montre une violation de cette règle.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)



