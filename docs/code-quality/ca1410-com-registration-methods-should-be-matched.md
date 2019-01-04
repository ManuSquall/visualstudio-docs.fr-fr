---
title: 'CA1410 : Méthodes d’inscription COM doivent être mises en correspondance.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1701ac1a432a9957e4350601ea55f13c6371147d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872893"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410 : Méthodes d’inscription COM doivent être mises en correspondance.

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type déclare une méthode qui est marquée avec le <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attribut mais ne déclare pas une méthode qui est marquée avec le <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attribut, ou vice versa.

## <a name="rule-description"></a>Description de la règle
 Pour les clients de composant COM (Object Model) créer un type .NET Framework, le type doit d’abord être enregistré. S’il est disponible, une méthode qui est marquée avec le <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> attribut est appelé pendant le processus d’inscription pour exécuter du code spécifié par l’utilisateur. Une méthode correspondante qui est marquée avec le <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> attribut est appelé pendant le processus d’inscription pour inverser les opérations de la méthode d’inscription.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez l’inscription correspondante ou la méthode de désinscription.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle. Le code commenté affiche le correctif de la violation.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Règles associées
 [CA1411 : Méthodes d’inscription COM ne doivent pas être visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Inscription d’assemblys dans COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (outil d’inscription d’assemblys)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)