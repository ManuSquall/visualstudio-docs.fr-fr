---
title: 'Ca1043 : utiliser un argument de chaîne ou intégral pour les indexeurs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03d21a824d2d3a9151dad139575f32e3417cbd39
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546833"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043 : Utiliser un argument de chaîne ou intégral pour les indexeurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient un indexeur public ou protected qui utilise un type d’index autre que <xref:System.Int32?displayProperty=fullName> , <xref:System.Int64?displayProperty=fullName> , <xref:System.Object?displayProperty=fullName> ou <xref:System.String?displayProperty=fullName> .

## <a name="rule-description"></a>Description de la règle
 Les indexeurs, c’est-à-dire les propriétés indexées, doivent utiliser des types de chaîne ou d’entier pour l’index. Ces types sont généralement utilisés pour l’indexation des structures de données et augmentent la convivialité de la bibliothèque. L’utilisation du <xref:System.Object> type doit être limitée aux cas où l’entier ou le type de chaîne spécifique ne peut pas être spécifié au moment de la conception. Si la conception requiert d’autres types pour l’index, reconsidérez si le type représente un magasin de données logiques. S’il ne représente pas un magasin de données logique, utilisez une méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez l’index par un type entier ou chaîne, ou utilisez une méthode au lieu de l’indexeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement après avoir soigneusement envisagé la nécessité de l’indexeur non standard.

## <a name="example"></a>Exemple
 L’exemple suivant montre un indexeur qui utilise un <xref:System.Int32> index.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1023 : Les indexeurs ne doivent pas être multidimensionnels](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024 : Utiliser les propriétés lorsque cela est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)
