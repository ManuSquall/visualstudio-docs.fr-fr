---
title: 'CA2145 : Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba7926f04f6112b28770110614fa18be88b028a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018161"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145 : Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une méthode transparente, une méthode qui est marquée avec le <xref:System.Security.SecuritySafeCriticalAttribute> (méthode), ou un type qui contient une méthode est marquée avec le <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribut.

## <a name="rule-description"></a>Description de la règle

Les méthodes décorées avec le <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribut ont un LinkDemand implicite sur toute méthode qui l’appelle. Ce LinkDemand requiert que le code appelant soit critique de sécurité. Marquage de la méthode qui utilise SuppressUnmanagedCodeSecurity avec le <xref:System.Security.SecurityCriticalAttribute> attribut rend cette spécification plus évidente pour les appelants de la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, marquez la méthode ou type portant le <xref:System.Security.SecurityCriticalAttribute> attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

### <a name="code"></a>Code

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]