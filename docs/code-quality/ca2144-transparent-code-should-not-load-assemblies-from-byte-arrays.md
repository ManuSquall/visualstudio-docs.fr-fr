---
title: "CA2144 : Le code transparent ne doit pas charger d'assemblys depuis des tableaux d'octets"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 971c7e794c5b782c2ba71be868fc2f9e7747fdb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542276"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144 : Le code transparent ne doit pas charger d'assemblys depuis des tableaux d'octets

|||
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|CheckId|CA2144|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode transparente charge un assembly à partir d’un tableau d’octets à l’aide d’une des méthodes suivantes :

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Description de la règle
 La révision de sécurité du code transparent n’est pas aussi complète que la révision de sécurité du code critique, car le code transparent ne peut pas exécuter d’actions relatives à la sécurité. Les assemblys chargés à partir d’un tableau d’octets peuvent ne pas être remarqués dans du code transparent, et ce tableau d’octets peut contenir du code critique, voire critique de sécurité, qui doit être audité. Par conséquent, le code transparent ne doit pas charger les assemblys à partir d’un tableau d’octets.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marquez la méthode qui charge l’assembly avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 Cette règle se déclenche sur le code suivant, car une méthode transparente charge un assembly à partir d’un tableau d’octets.

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]