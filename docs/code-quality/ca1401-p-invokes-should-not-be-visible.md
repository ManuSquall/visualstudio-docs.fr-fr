---
title: 'CA1401 : Les P-Invoke ne doivent pas être visibles'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e26daf68e0031358605427b310bb7284d43baf1b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922135"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401 : Les P/Invoke ne doivent pas être visibles

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Catégorie|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une méthode publique ou protégée dans un type public a l' <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attribut (également implémenté par le `Declare` mot clé [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]dans).

## <a name="rule-description"></a>Description de la règle
Les méthodes marquées avec l' <xref:System.Runtime.InteropServices.DllImportAttribute> attribut (ou les méthodes définies à l’aide du `Declare` mot clé [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]dans) utilisent les services d’appel de code non managé pour accéder au code non managé. De telles méthodes ne doivent pas être exposées. En gardant ces méthodes privées ou internes, vous vous assurez que votre bibliothèque ne peut pas être utilisée pour enfreindre la sécurité en permettant aux appelants d’accéder à des API non managées qu’ils n’ont pas pu appeler autrement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, modifiez le niveau d’accès de la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant déclare une méthode qui enfreint cette règle.

[!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]