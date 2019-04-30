---
title: 'CA1031 : Ne pas intercepter des types d’exception générale | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: 4588a949b4b6439c3f76270b0bcdab9cd52c23d9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431214"
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
> En commençant par le [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], le common language runtime (CLR) n’envoie plus d’exceptions d’état endommagé qui se produisent dans le système d’exploitation et le code managé, telles que des violations d’accès dans [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], pour être gérées par le code managé. Si vous voulez compiler une application dans le [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ou versions ultérieures et maintenir gestion des exceptions d’état endommagé, vous pouvez appliquer le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> d’attribut à la méthode qui gère l’exception d’état endommagé.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui enfreint cette règle et un type qui implémente correctement le `catch` bloc.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2200 : Lever à nouveau pour conserver les détails de la pile](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
