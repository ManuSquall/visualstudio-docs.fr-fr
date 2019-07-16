---
title: 'CA1802 : Utiliser des littéraux lorsque nécessaire | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5990d8ea3720098651d3ed696f6ee5ff907b82f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143146"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802 : Utilisez des littéraux quand cela est approprié
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un champ est déclaré `static` et `readonly` (`Shared` et `ReadOnly` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) et est initialisé avec une valeur qui est calculable à la compilation.

## <a name="rule-description"></a>Description de la règle
 La valeur d’un `static``readonly` champ est calculé à l’exécution lorsque le constructeur statique pour le type déclarant est appelé. Si le `static``readonly` champ est initialisé lorsqu’elle est déclarée et un constructeur statique n’est pas déclaré explicitement, le compilateur émet un constructeur statique pour initialiser le champ.

 La valeur d’un `const` champ est calculée au moment de la compilation et stockée dans les métadonnées, ce qui augmente les performances d’exécution lorsqu’elle est comparée à une `static``readonly` champ.

 La valeur assignée au champ ciblé étant calculable à la compilation, remplacez la déclaration par un `const` afin que la valeur soit calculée au moment de la compilation et non lors de l’exécution.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez le `static` et `readonly` modificateurs avec le `const` modificateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle, ou de désactiver la règle, si les performances ne sont pas un problème.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type, `UseReadOnly`, qui enfreint la règle et un type, `UseConstant`, qui satisfait la règle.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
