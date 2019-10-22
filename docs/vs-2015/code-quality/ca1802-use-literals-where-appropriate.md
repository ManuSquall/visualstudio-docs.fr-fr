---
title: 'Ca1802 : utilisez des littéraux quand cela est approprié | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bbcf83772a7a4031cf2e27abe7e8f4c08e21c11c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671511"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802 : Utilisez des littéraux lorsque nécessaire
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un champ est déclaré `static` et `readonly` (`Shared` et `ReadOnly` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), et est initialisé avec une valeur qui peut être calculée au moment de la compilation.

## <a name="rule-description"></a>Description de la règle
 La valeur d’un champ `static``readonly` est calculée au moment de l’exécution lorsque le constructeur statique du type déclarant est appelé. Si le champ `static``readonly` est initialisé lorsqu’il est déclaré et qu’un constructeur statique n’est pas déclaré explicitement, le compilateur émet un constructeur statique pour initialiser le champ.

 La valeur d’un champ `const` est calculée au moment de la compilation et stockée dans les métadonnées, ce qui augmente les performances d’exécution lorsqu’elle est comparée à un champ `static``readonly`.

 Étant donné que la valeur assignée au champ ciblé peut être calculée au moment de la compilation, remplacez la déclaration par un champ `const` afin que la valeur soit calculée au moment de la compilation plutôt qu’au moment de l’exécution.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez les modificateurs `static` et `readonly` par le modificateur `const`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle, ou de désactiver la règle, si les performances ne sont pas un problème.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type, `UseReadOnly`, qui enfreint la règle et un type, `UseConstant`, qui satisfait la règle.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
