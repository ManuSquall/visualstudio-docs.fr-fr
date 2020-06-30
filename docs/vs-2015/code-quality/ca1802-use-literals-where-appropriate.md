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
ms.openlocfilehash: dc8019c97d3c561000f1c6a8d083bee6253face3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544402"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802 : Utilisez des littéraux quand cela est approprié
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un champ est déclaré `static` et `readonly` ( `Shared` et `ReadOnly` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), et est initialisé avec une valeur qui peut être calculée au moment de la compilation.

## <a name="rule-description"></a>Description de la règle
 La valeur d’un `static``readonly` champ est calculée au moment de l’exécution lorsque le constructeur statique du type déclarant est appelé. Si le `static``readonly` champ est initialisé lorsqu’il est déclaré et qu’un constructeur statique n’est pas déclaré explicitement, le compilateur émet un constructeur statique pour initialiser le champ.

 La valeur d’un `const` champ est calculée au moment de la compilation et stockée dans les métadonnées, ce qui augmente les performances d’exécution lorsqu’il est comparé à un `static``readonly` champ.

 Étant donné que la valeur assignée au champ ciblé peut être calculée au moment de la compilation, remplacez la déclaration par un `const` champ afin que la valeur soit calculée au moment de la compilation plutôt qu’au moment de l’exécution.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez les `static` `readonly` modificateurs et par le `const` modificateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle, ou de désactiver la règle, si les performances ne sont pas un problème.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type, `UseReadOnly` , qui enfreint la règle et un type, `UseConstant` , qui satisfait la règle.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
