---
title: 'CA2200 : Rethrow pour conserver les détails de la pile | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5a79dd4f12a2d97cb707a38f4a46e5a20a8436b1
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589959"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200 : Levez à nouveau une exception pour conserver les détails de la pile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2200 : Rethrow pour conserver les détails de la pile](https://docs.microsoft.com/visualstudio/code-quality/ca2200-rethrow-to-preserve-stack-details).

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une exception est levée de nouveau et l’exception est explicitement spécifiée dans le `throw` instruction.

## <a name="rule-description"></a>Description de la règle
 Une fois qu’une exception est levée, partie des informations qu’il transporte est la trace de pile. La trace de pile est une liste de la hiérarchie d’appels de méthode qui commence par la méthode qui lève l’exception et se termine par la méthode qui intercepte l’exception. Si une exception est levée à nouveau en spécifiant l’exception dans le `throw` instruction, la trace de pile est redémarrée à la méthode actuelle et la liste d’appels de méthode entre la méthode d’origine qui a levé l’exception et la méthode actuelle est perdue. Pour conserver les informations de trace de pile d’origine avec l’exception, utilisez la `throw` instruction sans spécifier l’exception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, lever à nouveau l’exception sans spécifier explicitement.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode, `CatchAndRethrowExplicitly`, ce qui viole la règle et une méthode, `CatchAndRethrowImplicitly`, ce qui satisfait la règle.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]



