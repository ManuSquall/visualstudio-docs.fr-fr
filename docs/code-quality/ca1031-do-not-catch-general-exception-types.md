---
title: "CA1031 : Ne pas intercepter des types d’exception générale | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 681785bad04a9f16ca68a1f619700e143c01cb58
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031 : Ne pas intercepter des types d'exception générale
|||  
|-|-|  
|TypeName|DoNotCatchGeneralExceptionTypes|  
|CheckId|CA1031|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une exception générale comme <xref:System.Exception?displayProperty=fullName> ou <xref:System.SystemException?displayProperty=fullName> est interceptée dans un `catch` instruction ou une clause catch générale comme `catch()` est utilisé.  
  
## <a name="rule-description"></a>Description de la règle  
 Les exceptions générales ne doivent pas être interceptées.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, interceptez une exception plus spécifique ou levez à nouveau l’exception générale en tant que dernière instruction dans le `catch` bloc.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Types d’exception générale peut masquer des problèmes d’exécution de l’utilisateur de la bibliothèque et peut compliquer le débogage.  
  
> [!NOTE]
>  En commençant par le [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], le common language runtime (CLR) ne fournit plus les exceptions d’état endommagé qui se produisent dans le système d’exploitation et le code managé, telles que des violations d’accès dans [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], pour être gérées par le code managé. Si vous voulez compiler une application dans le [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] ou versions ultérieures et maintenir gestion des exceptions d’état endommagé, vous pouvez appliquer la <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> d’attribut à la méthode qui gère l’exception d’état endommagé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui viole cette règle et un type qui implémente correctement la `catch` bloc.  
  
 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA2200 : Levez à nouveau une exception pour conserver les détails de la pile](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)