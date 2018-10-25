---
title: 'CA2136 : Les membres ne doivent pas avoir d’annotations de transparence conflictuelles | Microsoft Docs'
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
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f524197fe647e148283e351924701ce7b11c4722
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894883"
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
 Cette règle se déclenche lorsqu’un membre de type est marqué avec un <xref:System.Security> attribut de sécurité qui a une transparence différente de celle de l’attribut de sécurité d’un conteneur du membre.

## <a name="rule-description"></a>Description de la règle
 Les attributs de transparence sont appliqués à partir d'éléments de code de plus grande portée à des éléments de plus petite portée. Les attributs de transparence d’éléments de code avec une plus grande portée sont prioritaires sur les attributs de transparence des éléments de code contenus dans le premier élément. Par exemple, une classe qui est marquée avec le <xref:System.Security.SecurityCriticalAttribute> attribut ne peut pas contenir une méthode qui est marquée avec le <xref:System.Security.SecuritySafeCriticalAttribute> attribut.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cette violation, supprimez l’attribut de sécurité de l’élément de code qui a une portée inférieure ou modifiez son attribut pour être le même que l’élément de code qui le contient.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas les avertissements de cette règle.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, une méthode est marquée avec le <xref:System.Security.SecuritySafeCriticalAttribute> attribut et il est membre d’une classe qui est marquée avec le <xref:System.Security.SecurityCriticalAttribute> attribut. L’attribut critique sécurisé doit être supprimé.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]



