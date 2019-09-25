---
title: 'CA1804 : Supprimez les variables locales inutilisées'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0a83d0afffc50c7697fad98c4dc49e31770d63d4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233752"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804 : Supprimez les variables locales inutilisées

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une méthode déclare une variable locale, mais n’utilise pas la variable, sauf éventuellement le destinataire d’une instruction d’assignation. Pour l’analyse par cette règle, l’assembly testé doit être généré avec des informations de débogage et le fichier de base de données du programme (. pdb) associé doit être disponible.

## <a name="rule-description"></a>Description de la règle
Les variables locales inutilisées et les assignations inutiles augmentent la taille d'un assembly et font baisser les performances.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez ou utilisez la variable locale.

> [!NOTE]
> Le C# compilateur supprime les variables locales inutilisées `optimize` lorsque l’option est activée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Supprimez un avertissement de cette règle si la variable a été émise par le compilateur. Il est également possible de supprimer un avertissement de cette règle, ou de désactiver la règle, si les performances et la maintenance du code ne sont pas des préoccupations principales.

## <a name="example"></a>Exemple
L’exemple suivant montre plusieurs variables locales inutilisées.

[!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
[!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA1809 Évitez les variables locales excessives](../code-quality/ca1809-avoid-excessive-locals.md)

[CA1811 Éviter le code privé qui n’a pas été appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812 Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801 Passer en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)