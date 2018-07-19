---
title: 'CA1804 : Supprimez les variables locales inutilisées'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a9212d4fd11a13e9905d0327e3c4c91413e2a8d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916769"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804 : Supprimez les variables locales inutilisées
|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode déclare une variable locale, mais n’utilise pas la variable sauf éventuellement en tant que le destinataire d’une instruction d’assignation. Pour l’analyse par cette règle, l’assembly testé doit être construit avec les informations de débogage et le fichier de base de données (.pdb) de programme associé doit être disponible.

## <a name="rule-description"></a>Description de la règle
 Les variables locales inutilisées et les assignations inutiles augmentent la taille d'un assembly et font baisser les performances.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez ou utilisez la variable locale. Notez que le compilateur c# qui est inclus avec [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] supprime les variables locales inutilisées lorsque le `optimize` est activée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle si la variable a été émise par un compilateur. Il est également recommandé de supprimer un avertissement de cette règle, ou pour désactiver la règle, si performances et maintenance du code ne sont pas des préoccupations.

## <a name="example"></a>Exemple
 L’exemple suivant montre plusieurs variables locales inutilisées.

 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1809 : Évitez le surplus de variables locales](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)