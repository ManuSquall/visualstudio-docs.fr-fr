---
title: 'CA1802 : Utiliser des littéraux lorsque nécessaire'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f86e19bc055a95b79f119f834d1d23d4f3a4e2c1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921716"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802 : Utiliser des littéraux lorsque nécessaire

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un champ est déclaré `static` et `readonly` (`Shared` et `ReadOnly` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) et est initialisé avec une valeur qui est calculable à la compilation.

## <a name="rule-description"></a>Description de la règle
 La valeur d’un `static``readonly` champ est calculé à l’exécution lorsque le constructeur statique pour le type déclarant est appelé. Si le `static``readonly` champ est initialisé lorsqu’elle est déclarée et un constructeur statique n’est pas déclaré explicitement, le compilateur émet un constructeur statique pour initialiser le champ.

 La valeur d’un `const` champ est calculée au moment de la compilation et stockée dans les métadonnées, ce qui augmente les performances d’exécution lorsqu’elle est comparée à une `static``readonly` champ.

 La valeur assignée au champ ciblé étant calculable à la compilation, remplacez la déclaration par un `const` afin que la valeur est calculée au moment de la compilation et non lors de l’exécution.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez le `static` et `readonly` modificateurs avec le `const` modificateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible sans supprimer un avertissement de cette règle, ou désactiver la règle, si les performances ne sont pas de problème.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type, `UseReadOnly`, qui enfreint la règle et un type, `UseConstant`, qui satisfait la règle.

 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]