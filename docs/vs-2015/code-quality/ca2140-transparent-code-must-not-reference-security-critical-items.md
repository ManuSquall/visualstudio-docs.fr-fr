---
title: 'CA2140 : Le code transparent ne doit pas faire référence à des éléments critiques de sécurité | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 82b58cc0287644a4ca21bf6333bf791b3c02e924
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951583"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140 : Le code transparent ne doit pas faire référence à des éléments critiques de sécurité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode transparente :

-   gère un type d’exception de sécurité critique de sécurité

-   a un paramètre qui est marqué comme un type critique de sécurité

-   a un paramètre générique avec des contraintes critiques de sécurité

-   a une variable locale d’un type critique de sécurité

-   fait référence à un type qui est marqué comme sécurité critiques

-   appelle une méthode qui est marquée en tant que de sécurité critiques

-   fait référence à un champ marqué comme de sécurité critique

-   Retourne un type qui est marqué comme sécurité critiques

## <a name="rule-description"></a>Description de la règle
 Un élément de code qui est marqué avec le <xref:System.Security.SecurityCriticalAttribute> attribut est critique de sécurité. Une méthode transparente ne peut pas utiliser un élément critique de sécurité. Si un type transparent essaie d’utiliser un type critique de sécurité un <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , ou <xref:System.FieldAccessException> est déclenché.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, effectuez l’une des opérations suivantes :

-   Marquer l’élément de code qui utilise le code critique de sécurité avec le <xref:System.Security.SecurityCriticalAttribute> attribut

     \- ou -

-   Supprimer le <xref:System.Security.SecurityCriticalAttribute> attribut à partir des éléments de code qui sont marqués comme sécurité critiques et à la place les marquer avec le <xref:System.Security.SecuritySafeCriticalAttribute> ou <xref:System.Security.SecurityTransparentAttribute> attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 Dans les exemples suivants, une méthode transparente tente de faire référence à une collection générique critique de sécurité, un champ critique de sécurité et une méthode critique de sécurité.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
