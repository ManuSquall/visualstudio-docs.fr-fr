---
title: 'CA2241 : fournissez des arguments corrects aux méthodes de mise en forme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 112065b2a8b9a88241ce62dda7b32a2f2c22fc75
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672026"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241 : Fournissez des arguments corrects aux méthodes de mise en forme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 L’argument de chaîne `format` passé à une méthode comme <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> ou <xref:System.String.Format%2A?displayProperty=fullName> ne contient pas d’élément de mise en forme qui correspond à chaque argument d’objet, ou vice versa.

## <a name="rule-description"></a>Description de la règle
 Les arguments des méthodes, telles que <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> et <xref:System.String.Format%2A> se composent d’une chaîne de format suivie de plusieurs instances de <xref:System.Object?displayProperty=fullName>. La chaîne de format se compose de texte et d’éléments de mise en forme incorporés sous la forme {index [, Alignment] [ : formatString]}. 'index’est un entier de base zéro qui indique les objets à mettre en forme. Si un objet n’a pas d’index correspondant dans la chaîne de format, l’objet est ignoré. Si l’objet spécifié par’index’n’existe pas, une <xref:System.FormatException?displayProperty=fullName> est levée au moment de l’exécution.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, fournissez un élément de mise en forme pour chaque argument d’objet et fournissez un argument d’objet pour chaque élément de mise en forme.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux violations de la règle.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
