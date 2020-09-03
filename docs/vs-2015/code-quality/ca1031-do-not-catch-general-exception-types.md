---
title: 'CA1031 : ne pas intercepter les types d’exception générale | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 520c9a066a4a902d5e9243baf1a8d8dec1b78e29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542400"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031 : Ne pas intercepter des types d'exception générale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Une exception générale, telle que <xref:System.Exception?displayProperty=fullName> ou <xref:System.SystemException?displayProperty=fullName> , est interceptée dans une `catch` instruction, ou une clause catch générale telle que `catch()` est utilisée.

## <a name="rule-description"></a>Description de la règle
 Les exceptions générales ne doivent pas être interceptées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, interceptez une exception plus spécifique ou levez à nouveau l’exception générale comme dernière instruction dans le `catch` bloc.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. L’interception des types d’exception généraux peut masquer les problèmes d’exécution de l’utilisateur de la bibliothèque et peut rendre le débogage plus difficile.

> [!NOTE]
> À compter de [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] , le Common Language Runtime (CLR) ne remet plus les exceptions d’état endommagé qui se produisent dans le système d’exploitation et le code managé, telles que les violations d’accès dans [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] , qui sont gérées par le code managé. Si vous souhaitez compiler une application dans le [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ou versions ultérieures et maintenir la gestion des exceptions d’état endommagé, vous pouvez appliquer l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attribut à la méthode qui gère l’exception d’état endommagé.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui enfreint cette règle et un type qui implémente correctement le `catch` bloc.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2200 : Levez à nouveau une exception pour conserver les détails de la pile](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
