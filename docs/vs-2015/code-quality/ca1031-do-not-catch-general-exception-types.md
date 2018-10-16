---
title: 'CA1031 : Ne pas intercepter des types d’exception générale | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 630bd84f4b5ceaa3719aa0e19d7d64bb08423127
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258351"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031 : Ne pas intercepter des types d'exception générale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une exception générale comme <xref:System.Exception?displayProperty=fullName> ou <xref:System.SystemException?displayProperty=fullName> est interceptée dans un `catch` instruction ou une clause catch générale comme `catch()` est utilisé.

## <a name="rule-description"></a>Description de la règle
 Les exceptions générales ne doivent pas être interceptées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, interceptez une exception plus spécifique ou levez à nouveau l’exception générale en tant que la dernière instruction dans le `catch` bloc.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Interception de types d’exception générale peut masquer des problèmes d’exécution à partir de l’utilisateur de la bibliothèque et peut compliquer le débogage.

> [!NOTE]
>  En commençant par le [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], le common language runtime (CLR) n’envoie plus d’exceptions d’état endommagé qui se produisent dans le système d’exploitation et le code managé, telles que des violations d’accès dans [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], pour être gérées par le code managé. Si vous voulez compiler une application dans le [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ou versions ultérieures et maintenir gestion des exceptions d’état endommagé, vous pouvez appliquer le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> d’attribut à la méthode qui gère l’exception d’état endommagé.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui enfreint cette règle et un type qui implémente correctement le `catch` bloc.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2200 : Levez à nouveau une exception pour conserver les détails de la pile](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)



