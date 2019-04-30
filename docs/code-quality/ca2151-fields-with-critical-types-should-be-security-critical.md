---
title: 'CA2151 : Les champs avec des types critiques doivent être des champs critiques de sécurité'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b75425d35e51125b0cfe1f76c8c18d7f155a12c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796737"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151 : Les champs avec des types critiques doivent être des champs critiques de sécurité

|||
|-|-|
|TypeName||
|CheckId|CA2151|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un champ transparent de sécurité ou un champ critique sécurisé est déclaré. Son type est spécifié comme critique de sécurité. Exemple :

```csharp
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      Type1 m_field; // CA2151, transparent field of critical type
   }
```

Dans cet exemple, `m_field` est un champ transparent de sécurité d'un type critique de sécurité.

## <a name="rule-description"></a>Description de la règle

Pour utiliser les types critiques de sécurité, le code qui référence le type doit être critique de sécurité ou critique sécurisé. Ceci est vrai même si la référence est indirecte. Par exemple, lorsque vous faites référence à un champ transparent de type critique, votre code doit être critique de sécurité ou critique sécurisé. Par conséquent, un champ transparent de sécurité ou critique sécurisé est trompeur, car le code transparent ne pourra toujours pas accéder au champ.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, marquez le champ avec le <xref:System.Security.SecurityCriticalAttribute> d’attribut, ou rendez le type qui est référencé par le champ soit sécurité transparente ou sans échec critique.

```csharp
// Fix 1: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

// Fix 2: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   class Type1 { } // Type1 is now transparent

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }
```

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

### <a name="code"></a>Code

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]