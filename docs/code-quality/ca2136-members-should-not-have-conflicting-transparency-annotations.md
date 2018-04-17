---
title: 'CA2136 : Les membres ne doivent pas avoir d’annotations de transparence conflictuelles | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6b77dfdbb97d54e5ad1ac31d3f5e29a03cd9b54
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136 : Les membres ne doivent pas avoir d'annotations de transparence conflictuelles
|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|CheckId|CA2136|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Cette règle se déclenche lorsqu’un membre de type est marqué avec un <xref:System.Security> l’attribut de sécurité qui a une transparence différente de celle de l’attribut de sécurité d’un conteneur du membre.  
  
## <a name="rule-description"></a>Description de la règle  
 Les attributs de transparence sont appliqués à partir d'éléments de code de plus grande portée à des éléments de plus petite portée. Les attributs de transparence d’éléments de code avec une plus grande portée sont prioritaires sur les attributs de transparence des éléments de code contenus dans le premier élément. Par exemple, une classe qui est marquée avec la <xref:System.Security.SecurityCriticalAttribute> attribut ne peut pas contenir une méthode qui est marquée avec le <xref:System.Security.SecuritySafeCriticalAttribute> attribut.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour résoudre cette violation, supprimez l’attribut de sécurité de l’élément de code qui a une portée inférieure ou modifiez son attribut pour être le même que l’élément de code contenant.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, une méthode est marquée avec la <xref:System.Security.SecuritySafeCriticalAttribute> attribut et il est membre d’une classe qui est marqué avec la <xref:System.Security.SecurityCriticalAttribute> attribut. L’attribut critique sécurisé doit être supprimé.  
  
 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]