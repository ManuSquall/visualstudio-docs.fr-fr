---
title: 'CA1810 : Initialisez les champs statiques de type référence en ligne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b31a0bbea244d5d196364517b5c5a2ca8d7a53a1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914638"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810 : Initialisez les champs statiques de type référence en ligne
|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type référence déclare un constructeur statique explicite.

## <a name="rule-description"></a>Description de la règle
 Lorsqu’un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d’instances du type afin de garantir que le constructeur statique a été appelé précédemment. L’initialisation statique est déclenchée lorsqu’un membre statique est accessible ou lorsqu’une instance du type est créée. Toutefois, l’initialisation statique n’est pas déclenchée si vous déclarez une variable du type, mais ne l’utilisez pas, ce qui peut être important si l’initialisation modifie l’état global.

 Lorsque toutes les données statiques sont initialisées inline et un constructeur statique explicite n’est pas déclaré, les compilateurs de langage intermédiaire MSIL Microsoft ajoutent la `beforefieldinit` indicateur et un constructeur statique implicit qui initialise les données statiques, pour le type MSIL définition. Lorsque le compilateur JIT rencontre le `beforefieldinit` indicateur, la plupart du temps, les vérifications des constructeurs statiques ne sont pas ajoutées. L’initialisation statique est garantie à un moment donné avant d’accéder à tous les champs statiques, mais pas avant l’appel d’un constructeur d’instance ou de méthode statique. Notez que l’initialisation statique peut se produire à tout moment après la déclaration d’une variable du type.

 Les vérifications des constructeurs statiques peuvent diminuer les performances. Souvent, un constructeur statique est utilisé uniquement pour initialiser les champs statiques, auquel cas vous devez seulement vous assurer que l’initialisation statique se produit avant le premier accès d’un champ statique. Le `beforefieldinit` comportement est approprié pour celles-ci et d’autres types. Il ne convient uniquement lorsque l’initialisation statique affecte l’état global et une des conditions suivantes est remplie :

-   L’effet sur l’état global est coûteuse et n’est pas obligatoire si le type n’est pas utilisé.

-   Les effets de l’état global sont accessibles sans accéder à tous les champs statiques de type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si les performances ne sont pas un problème ; ou si les modifications de l’état global provoqués par l’initialisation statique sont coûteuses ou doivent être garantie avant l’appel d’une méthode statique du type ou une instance du type est créée.

## <a name="example"></a>Exemple
 L’exemple suivant présente un type, `StaticConstructor`, qui enfreint la règle et un type, `NoStaticConstructor`, qui remplace le constructeur statique d’une initialisation inline pour satisfaire la règle.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

 Notez l’ajout de la `beforefieldinit` indicateur sur la définition MSIL pour la `NoStaticConstructor` classe.

 **.class public auto ansi StaticConstructor** **étend [mscorlib**
 **{**
 **} / / de fin de la classe StaticConstructor** 
 **.class public auto ansi beforefieldinit NoStaticConstructor** **étend [mscorlib**
 **{** 
 **} / / de fin de la classe NoStaticConstructor**
## <a name="related-rules"></a>Règles associées
 [CA2207 : Initialisez les champs statiques des types de valeurs inline](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)