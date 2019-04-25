---
title: 'CA1810 : Initialiser des champs statiques de type référence en ligne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dd0372ca3264bedd6fbb17ef3c8326471cb6e99f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60037866"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810 : Initialisez les champs statiques de type référence en ligne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type référence déclare un constructeur statique explicite.

## <a name="rule-description"></a>Description de la règle
 Lorsqu'un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d'instances du type afin de garantir que le constructeur statique a été appelé précédemment. L’initialisation statique est déclenchée lorsqu’un membre statique est accessible ou lorsqu’une instance du type est créée. Toutefois, l’initialisation statique n’est pas déclenchée si vous déclarez une variable du type, mais ne l’utilisez pas, ce qui peut être important si l’initialisation modifie l’état global.

 Lorsque toutes les données statiques sont initialisées inline et un constructeur statique explicite n’est pas déclaré, les compilateurs Microsoft intermediate language (MSIL) ajoutent le `beforefieldinit` indicateur et un constructeur statique implicit qui initialise les données statiques, pour le type MSIL définition. Lorsque le compilateur JIT rencontre le `beforefieldinit` indicateur, la plupart du temps, les vérifications du constructeur statique ne sont pas ajoutées. L’initialisation statique est garantie à un moment avant que tous les champs statiques sont accessibles, mais pas avant un constructeur d’instance ou méthode statique est appelé. Notez que l’initialisation statique peut se produire à tout moment après la déclaration d’une variable du type.

 Les vérifications des constructeurs statiques peuvent diminuer les performances. Un constructeur statique est souvent utilisé uniquement pour initialiser des champs statiques, auquel cas vous devez uniquement vous assurer que l’initialisation statique se produit avant le premier accès d’un champ statique. Le `beforefieldinit` comportement est approprié pour celles-ci et la plupart des autres types. Il est inadapté uniquement lors de l’initialisation statique affecte l’état global et une des opérations suivantes est remplie :

- L’effet sur l’état global est coûteuse et n’est pas obligatoire si le type n’est pas utilisé.

- Les effets de l’état global sont accessibles sans accéder à tous les champs statiques du type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si les performances ne sont pas un problème ; ou si les modifications d’état global qui sont provoquées par l’initialisation statique sont coûteuses ou doivent être garantie avant une méthode statique du type est appelée ou une instance du type est créée.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type, `StaticConstructor`, qui enfreint la règle et un type, `NoStaticConstructor`, qui remplace le constructeur statique par l’initialisation inline pour satisfaire la règle.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 Notez l’ajout de la `beforefieldinit` indicateur sur la définition MSIL pour la `NoStaticConstructor` classe.

 **.class public auto ansi StaticConstructor** **étend [mscorlib**
 **{**
 **} / de fin de la classe StaticConstructor** 
 **.class public auto ansi beforefieldinit NoStaticConstructor** **étend [mscorlib**
 **{** 
 **} / de fin de la classe NoStaticConstructor**
## <a name="related-rules"></a>Règles associées
 [CA2207 : Initialiser des champs statiques de type valeur en ligne](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)
