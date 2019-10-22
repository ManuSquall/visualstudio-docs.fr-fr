---
title: 'CA1810 : initialisez les champs statiques de type référence en ligne | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9032ac105477370477b13554afe4ee65bd7cd733
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609017"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810 : Initialisez les champs statiques de type référence en ligne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type référence déclare un constructeur statique explicite.

## <a name="rule-description"></a>Description de la règle
 Lorsqu'un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d'instances du type afin de garantir que le constructeur statique a été appelé précédemment. L’initialisation statique est déclenchée lors de l’accès à un membre statique ou lors de la création d’une instance du type. Toutefois, l’initialisation statique n’est pas déclenchée si vous déclarez une variable du type, mais que vous ne l’utilisez pas, ce qui peut être important si l’initialisation modifie l’état global.

 Lorsque toutes les données statiques sont initialisées en ligne et qu’un constructeur statique explicite n’est pas déclaré, les compilateurs MSIL (Microsoft Intermediate Language) ajoutent l’indicateur `beforefieldinit` et un constructeur statique implicite, qui initialise les données statiques, en type MSIL définition. Quand le compilateur JIT rencontre l’indicateur `beforefieldinit`, la plupart du temps, les vérifications du constructeur statique ne sont pas ajoutées. L’initialisation statique est garantie à un moment donné avant l’accès à tous les champs statiques, mais pas avant l’appel d’une méthode ou d’un constructeur d’instance statique. Notez que l’initialisation statique peut se produire à tout moment après la déclaration d’une variable du type.

 Les vérifications des constructeurs statiques peuvent diminuer les performances. Souvent, un constructeur statique est utilisé uniquement pour initialiser des champs statiques. dans ce cas, vous devez uniquement vérifier que l’initialisation statique se produit avant le premier accès à un champ statique. Le comportement `beforefieldinit` convient à ces types et à la plupart des autres types. Elle n’est pas appropriée lorsque l’initialisation statique affecte l’état global et que l’une des conditions suivantes est vraie :

- L’effet sur l’état global est onéreux et n’est pas requis si le type n’est pas utilisé.

- Les effets d’État globaux sont accessibles sans accéder aux champs statiques du type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si les performances ne sont pas un problème ; ou si les modifications d’État globales provoquées par l’initialisation statique sont coûteuses ou doivent être garanties avant qu’une méthode statique du type soit appelée ou qu’une instance du type soit créée.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type, `StaticConstructor`, qui enfreint la règle et un type, `NoStaticConstructor`, qui remplace le constructeur statique par l’initialisation Inline pour satisfaire la règle.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 Notez l’ajout de l’indicateur `beforefieldinit` sur la définition MSIL pour la classe `NoStaticConstructor`.

 **. la classe public auto ANSI StaticConstructor** **étend [mscorlib] System. Object** 
 **{** 
 **}//End of Class StaticConstructor** 
 **. Class public auto ANSI beforefieldinit NoStaticConstructor** ** étend [mscorlib] System. Object** 
 **{** 1 **}//End of Class NoStaticConstructor**
## <a name="related-rules"></a>Règles associées
 [CA2207 : Initialisez les champs statiques des types de valeurs inline](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)
