---
title: 'Ca1401 : les appels P ne doivent pas être visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9f13669959a5874c74753d304371b8ab7db14d4e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547288"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401 : Les P/Invoke ne doivent pas être visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée dans un type public a l' <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attribut (également implémenté par le `Declare` mot clé dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="rule-description"></a>Description de la règle
 Les méthodes marquées avec l' <xref:System.Runtime.InteropServices.DllImportAttribute> attribut (ou les méthodes définies à l’aide du `Declare` mot clé dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) utilisent les services d’appel de code non managé pour accéder au code non managé. De telles méthodes ne doivent pas être exposées. En gardant ces méthodes privées ou internes, vous vous assurez que votre bibliothèque ne peut pas être utilisée pour enfreindre la sécurité en permettant aux appelants d’accéder à des API non managées qu’ils n’ont pas pu appeler autrement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez le niveau d’accès de la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant déclare une méthode qui enfreint cette règle.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]
