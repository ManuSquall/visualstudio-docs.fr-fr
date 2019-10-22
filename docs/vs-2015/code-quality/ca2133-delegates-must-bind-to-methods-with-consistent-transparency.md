---
title: 'CA2133 : les délégués doivent être liés aux méthodes avec une transparence cohérente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 487047b7dd3096e65a6e287d79d91d3029f3dc5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608996"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133 : Les délégués doivent lier les méthodes avec une transparence cohérente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

> [!NOTE]
> Cet avertissement est appliqué uniquement au code qui exécute CoreCLR (la version du CLR qui est spécifique aux applications Web Silverlight).

## <a name="cause"></a>Cause
 Cet avertissement se déclenche sur une méthode qui lie un délégué marqué avec l' <xref:System.Security.SecurityCriticalAttribute> à une méthode transparente ou marquée avec la <xref:System.Security.SecuritySafeCriticalAttribute>. L’avertissement déclenche également une méthode qui lie un délégué transparent ou critique sécurisé à une méthode critique.

## <a name="rule-description"></a>Description de la règle
 Les types délégués et les méthodes auxquelles ils sont liés doivent avoir une transparence cohérente. Les délégués transparents et critiques sécurisés ne peuvent être liés qu’à d’autres méthodes transparentes ou critiques sécurisées. De même, les délégués critiques ne peuvent être liés qu’à des méthodes critiques. Ces règles de liaison garantissent que le seul code qui peut appeler une méthode via un délégué pourrait également appeler la même méthode directement. Par exemple, les règles de liaison empêchent le code transparent d’appeler directement du code critique via un délégué transparent.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cet avertissement, modifiez la transparence du délégué ou de la méthode qu’il lie afin que la transparence des deux soit équivalente.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]
