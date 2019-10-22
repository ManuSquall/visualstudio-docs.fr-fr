---
title: 'CA2136 : les membres ne doivent pas avoir d’annotations de transparence conflictuelles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f2fbb856ff53552ab99dabd4f650e9fd7f62a088
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602966"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136 : Les membres ne doivent pas avoir d'annotations de transparence conflictuelles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Cette règle se déclenche lorsqu’un membre de type est marqué avec un attribut de sécurité <xref:System.Security> qui a une transparence différente de l’attribut de sécurité d’un conteneur du membre.

## <a name="rule-description"></a>Description de la règle
 Les attributs de transparence sont appliqués à partir d’éléments de code de plus grande portée à des éléments de plus petite portée. Les attributs de transparence d’éléments de code avec une plus grande portée sont prioritaires sur les attributs de transparence des éléments de code contenus dans le premier élément. Par exemple, une classe marquée avec l’attribut <xref:System.Security.SecurityCriticalAttribute> ne peut pas contenir une méthode marquée avec l’attribut <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre ce problème, supprimez l’attribut de sécurité de l’élément de code qui a une portée inférieure, ou modifiez son attribut pour qu’il soit identique à l’élément de code conteneur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas les avertissements de cette règle.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, une méthode est marquée avec l’attribut <xref:System.Security.SecuritySafeCriticalAttribute> et il est membre d’une classe qui est marquée avec l’attribut <xref:System.Security.SecurityCriticalAttribute>. L’attribut Security SAFE doit être supprimé.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
