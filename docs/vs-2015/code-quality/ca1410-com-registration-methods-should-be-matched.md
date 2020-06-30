---
title: 'CA1410 : les méthodes d’inscription COM doivent être mises en correspondance | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 43767ce04b32440a5c6753f5bfcabb91487c1232
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546703"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410 : Les méthodes d'inscription COM doivent être mises en correspondance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type déclare une méthode marquée avec l' <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attribut, mais ne déclare pas une méthode marquée avec l' <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attribut, ou vice versa.

## <a name="rule-description"></a>Description de la règle
 Pour que les clients COM (Component Object Model) créent un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] type, le type doit d’abord être enregistré. S’il est disponible, une méthode marquée avec l' <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> attribut est appelée pendant le processus d’inscription pour exécuter le code spécifié par l’utilisateur. Une méthode correspondante marquée avec l' <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> attribut est appelée pendant le processus d’annulation de l’inscription pour inverser les opérations de la méthode d’inscription.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez la méthode d’inscription ou d’annulation d’inscription correspondante.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle. Le code commenté indique le correctif pour la violation.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1411 : Les méthodes d'inscription COM ne doivent pas être visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[Inscription d’assemblys à l’aide deRegasm.exe com](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [(outil d’inscription d’assembly)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
