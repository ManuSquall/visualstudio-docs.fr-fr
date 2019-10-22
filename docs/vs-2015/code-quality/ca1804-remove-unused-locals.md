---
title: 'CA1804 : supprimez les variables locales inutilisées | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 824a65e765f21748b97292beea64ea6c9bd64a1b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671561"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804 : Supprimez les variables locales inutilisées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Pour corriger une violation de cette règle, supprimez ou utilisez la variable locale. Notez que le C# compilateur inclus avec [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] supprime les variables locales inutilisées lorsque l’option `optimize` est activée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle si la variable a été émise par le compilateur. Il est également possible de supprimer un avertissement de cette règle, ou de désactiver la règle, si les performances et la maintenance du code ne sont pas des préoccupations principales.

## <a name="example"></a>Exemple
 L’exemple suivant montre plusieurs variables locales inutilisées.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1809 : Évitez le surplus de variables locales](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)
