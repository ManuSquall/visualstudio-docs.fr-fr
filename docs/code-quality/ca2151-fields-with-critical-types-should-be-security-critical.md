---
title: "CA2151 : les champs avec des types critiques doivent &#234;tre des champs critiques de s&#233;curit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 4
---
# CA2151 : les champs avec des types critiques doivent &#234;tre des champs critiques de s&#233;curit&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName||  
|CheckId|CA2151|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## Cause  
 Un champ transparent de sécurité ou un champ critique sécurisé est déclaré.  Son type est spécifié comme critique de sécurité.  Par exemple :  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      Type1 m_field; // CA2151, transparent field of critical type  
   }  
  
```  
  
 Dans cet exemple, `m_field` est un champ transparent de sécurité d'un type critique de sécurité.  
  
## Description de la règle  
 Pour utiliser les types critiques de sécurité, le code qui référence le type doit être critique de sécurité ou critique sécurisé.  Ceci est vrai même si la référence est indirecte.  Par exemple, lorsque vous faites référence à un champ transparent de type critique, votre code doit être critique de sécurité ou critique sécurisé.  Par conséquent, un champ transparent de sécurité ou critique sécurisé est trompeur, car le code transparent ne pourra toujours pas accéder au champ.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, marquez le champ avec l'attribut <xref:System.Security.SecurityCriticalAttribute> ou faites en sorte que le type référencé par le champ soit transparent de sécurité ou critique sécurisé.  
  
```c#  
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
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
### Code  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]  
  
### Commentaires