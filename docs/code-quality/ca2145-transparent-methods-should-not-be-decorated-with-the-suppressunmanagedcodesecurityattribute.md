---
title: 'CA2145 : Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9269a0862dacf928cffb31f722f382271d5f0e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542117"
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