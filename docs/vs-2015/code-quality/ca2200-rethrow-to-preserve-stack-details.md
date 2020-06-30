---
title: 'Ca2200 : lever à nouveau pour conserver les détails de la pile | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6d63ef6ff3647742e931fd05f59c66b40059ad00
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546365"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200 : Levez à nouveau une exception pour conserver les détails de la pile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une exception est levée à nouveau et l’exception est explicitement spécifiée dans l' `throw` instruction.

## <a name="rule-description"></a>Description de la règle
 Une fois qu’une exception est levée, une partie des informations qu’elle contient est la trace de la pile. La trace de la pile est une liste de la hiérarchie d’appels de méthode qui commence par la méthode qui lève l’exception et se termine par la méthode qui intercepte l’exception. Si une exception est levée à nouveau en spécifiant l’exception dans l' `throw` instruction, la trace de la pile est redémarrée au niveau de la méthode actuelle et la liste des appels de méthode entre la méthode d’origine qui a levé l’exception et la méthode actuelle est perdue. Pour conserver les informations de trace de la pile d’origine avec l’exception, utilisez l' `throw` instruction sans spécifier l’exception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, levez à nouveau l’exception sans spécifier explicitement l’exception.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode, `CatchAndRethrowExplicitly` , qui enfreint la règle et une méthode, `CatchAndRethrowImplicitly` , qui satisfait la règle.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
