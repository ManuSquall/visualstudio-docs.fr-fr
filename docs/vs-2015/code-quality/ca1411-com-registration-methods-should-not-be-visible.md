---
title: 'CA1411 : Les méthodes d’inscription COM ne doivent pas être visibles | Microsoft Docs'
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
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3f42bc0f6434cb67a3b6796e78a08cd874f436b7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225694"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411 : Les méthodes d'inscription COM ne doivent pas être visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode qui est marquée avec le <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attribut est visible de l’extérieur.

## <a name="rule-description"></a>Description de la règle
 Lorsqu’un assembly est inscrit avec COM Component Object Model (), les entrées sont ajoutées au Registre pour chaque type visible par COM dans l’assembly. Les méthodes marquées avec le <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> et <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> attributs sont appelées pendant les processus d’inscription et d’annulation d’inscription, respectivement, pour exécuter le code utilisateur qui est spécifique à l’inscription/la désinscription de ces types. Ce code ne doit pas être appelé en dehors de ces processus.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez l’accessibilité de la méthode à `private` ou `internal` (`Friend` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux méthodes qui enfreignent la règle.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1410 : Les méthodes d’inscription COM doivent être mises en correspondance](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Inscription d’assemblys dans COM](http://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (outil Assembly Registration Tool)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)



