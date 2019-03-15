---
title: 'CA1802 : Utilisez des littéraux quand cela est approprié'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f4dbafb4c6f7ad590244842ac3def0e26f8a14fd
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57872964"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802 : Utilisez des littéraux quand cela est approprié

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un champ est déclaré `static` et `readonly` (`Shared` et `ReadOnly` en Visual Basic) et est initialisé avec une valeur qui est calculable à la compilation.

Par défaut, cette règle examine uniquement les champs visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

La valeur d’un `static readonly` champ est calculé à l’exécution lorsque le constructeur statique pour le type déclarant est appelé. Si le `static readonly` champ est initialisé lorsqu’elle est déclarée et un constructeur statique n’est pas déclaré explicitement, le compilateur émet un constructeur statique pour initialiser le champ.

La valeur d’un `const` champ est calculée au moment de la compilation et stockée dans les métadonnées, ce qui augmente les performances d’exécution lorsqu’elle est comparée à une `static readonly` champ.

La valeur assignée au champ ciblé étant calculable à la compilation, remplacez la déclaration par un `const` afin que la valeur soit calculée au moment de la compilation et non lors de l’exécution.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, remplacez le `static` et `readonly` modificateurs avec le `const` modificateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle, ou de désactiver la règle, si les performances ne sont pas un problème.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca1802.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (performances). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre un type, `UseReadOnly`, qui enfreint la règle et un type, `UseConstant`, qui satisfait la règle.

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]