---
title: 'CA2241 : Fournissez des arguments corrects aux méthodes de mise en forme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6ef5b2f3b7244762e69d87882cbf2caae63cb34b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547878"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241 : Fournissez des arguments corrects aux méthodes de mise en forme

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le `format` chaîne argument passé à une méthode telle que <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, ou <xref:System.String.Format%2A?displayProperty=fullName> ne contient pas un élément de format qui correspond à chaque argument d’objet, ou vice versa.

## <a name="rule-description"></a>Description de la règle
 Les arguments de méthodes telles que <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, et <xref:System.String.Format%2A> se composent d’une chaîne de format suivie par plusieurs <xref:System.Object?displayProperty=fullName> instances. La chaîne de format se compose de texte et d’éléments de format incorporé du formulaire, {index [, alignment] [ : formatString]}. « index » est un entier de base zéro qui indique les objets à mettre en forme. Si un objet n’a pas d’un index correspondant dans la chaîne de format, l’objet est ignoré. Si l’objet spécifié par « index » n’existe pas, un <xref:System.FormatException?displayProperty=fullName> est levée lors de l’exécution.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, fournissez un élément de format pour chaque argument d’objet et fournir un argument d’objet pour chaque élément de format.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux violations de la règle.

 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]