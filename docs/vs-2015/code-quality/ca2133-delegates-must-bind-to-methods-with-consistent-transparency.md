---
title: 'CA2133 : Les délégués doivent lier les méthodes avec une transparence cohérente | Microsoft Docs'
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
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7ed73973125216e8f6056de8f104d9cbce98334f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590054"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133 : Les délégués doivent lier les méthodes avec une transparence cohérente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2133 : les délégués doivent lier aux méthodes avec une transparence cohérente](https://docs.microsoft.com/visualstudio/code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency).

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

> [!NOTE]
>  Cet avertissement est appliqué uniquement au code qui est en cours d’exécution CoreCLR (la version du CLR qui est spécifique aux applications Silverlight Web).

## <a name="cause"></a>Cause
 Cet avertissement se déclenche sur une méthode qui lie un délégué qui est marquée avec le <xref:System.Security.SecurityCriticalAttribute> à une méthode qui est transparente ou marquée avec le <xref:System.Security.SecuritySafeCriticalAttribute>. L’avertissement déclenche également une méthode qui lie un délégué transparent ou critique sécurisé à une méthode critique.

## <a name="rule-description"></a>Description de la règle
 Types délégués et les méthodes auxquelles elles se lient doivent avoir une transparence cohérente. Délégués transparents et critiques sécurisés peuvent uniquement lier à d’autres méthodes transparents ou critique sécurisé. De même, les délégués critiques peuvent lier uniquement des méthodes critiques. Ces règles de liaison garantissent que le seul code que vous pouvez appeler une méthode via un délégué aurait également pu appeler la même méthode directement. Par exemple, les règles de liaison empêchent le code transparent de l’appel de code critique directement par le biais d’un délégué transparent.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cet avertissement, modifiez la transparence du délégué ou de la méthode qu’il lie afin que la transparence des deux sont équivalentes.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]



