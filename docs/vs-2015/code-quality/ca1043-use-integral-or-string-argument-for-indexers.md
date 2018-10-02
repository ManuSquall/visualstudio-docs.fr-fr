---
title: 'CA1043 : Utiliser l’argument de chaîne ou intégral pour les indexeurs | Microsoft Docs'
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
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9fb73f52e2b3f74b5c76cb2218baa5a6cd170706
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588106"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043 : Utiliser un argument de chaîne ou intégral pour les indexeurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1043 : utiliser l’argument de chaîne ou intégral pour les indexeurs](https://docs.microsoft.com/visualstudio/code-quality/ca1043-use-integral-or-string-argument-for-indexers).

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contienne un indexeur public ou protégé qui utilise un type d’index autre que <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, ou <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 Les indexeurs, autrement dit, les propriétés indexées, doivent utiliser des types entier ou chaîne pour l’index. Ces types sont généralement utilisés pour indexer des structures de données et augmentent la facilité d’utilisation de la bibliothèque. Utilisation de la <xref:System.Object> type doit être limité aux cas où le type entier ou une chaîne spécifique ne peut pas être spécifié au moment du design. Si la conception nécessite d’autres types pour l’index, reconsidérez si le type représente un magasin de données logique. Si elle ne représente pas un magasin de données logique, utilisez une méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifier l’index à un type entier ou chaîne, ou utilisez une méthode au lieu de l’indexeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle uniquement après avoir soigneusement envisagé la nécessité de l’indexeur non standard.

## <a name="example"></a>Exemple
 L’exemple suivant montre un indexeur qui utilise un <xref:System.Int32> index.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1023 : Les indexeurs ne doivent pas être multidimensionnels](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024 : Utilisez des propriétés quand c’est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)



