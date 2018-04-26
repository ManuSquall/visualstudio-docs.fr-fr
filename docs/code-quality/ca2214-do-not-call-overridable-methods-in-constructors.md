---
title: "CA2214 : N'appelez pas de méthodes substituables dans les constructeurs"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5ebcd4164f9db28d4cb1f150ee3a4bb21b21cde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214 : N'appelez pas de méthodes substituables dans les constructeurs
|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le constructeur d’un type unsealed appelle une méthode virtuelle définie dans sa classe.

## <a name="rule-description"></a>Description de la règle
 Lorsqu’une méthode virtuelle est appelée, le type réel qui exécute la méthode n’est pas sélectionné jusqu’au moment de l’exécution. Lorsqu’un constructeur appelle une méthode virtuelle, il est possible que le constructeur de l’instance qui appelle la méthode n’a pas été exécutée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, n’appelez pas les méthodes virtuelles d’un type à partir de dans les constructeurs du type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Le constructeur doit être refondu pour éliminer l’appel à la méthode virtuelle.

## <a name="example"></a>Exemple
 L’exemple suivant montre l’effet de la violation de cette règle. L’application de test crée une instance de `DerivedType`, ce qui entraîne sa classe de base (`BadlyConstructedType`) constructeur à exécuter. `BadlyConstructedType`du constructeur appelle la méthode virtuelle de manière incorrecte `DoSomething`. Comme le montre la sortie, `DerivedType.DoSomething()` s’exécute et par conséquent, avant `DerivedType`du constructeur s’exécute.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

 Cet exemple produit la sortie suivante.

 **Appel de constructeur de base. ** 
 **DoSomething de dérivé est appelé - initialisé ? Ne**
**appel dérivée ctor.**