---
title: "CA2144&#160;: Le code transparent ne doit pas charger d&#39;assemblys depuis des tableaux d&#39;octets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2144"
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA2144&#160;: Le code transparent ne doit pas charger d&#39;assemblys depuis des tableaux d&#39;octets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|  
|CheckId|CA2144|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode transparente charge un assembly à partir d'un tableau d'octets à l'aide de l'une des méthodes suivantes :  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
## Description de la règle  
 La révision de sécurité du code transparent n'est pas aussi complète que la révision de sécurité du code critique, car le code transparent ne peut pas exécuter d'actions relatives à la sécurité.  Les assemblys chargés à partir d'un tableau d'octets peuvent ne pas être remarqués dans du code transparent, et ce tableau d'octets peut contenir du code critique, voire critique de sécurité, qui doit être audité.  Par conséquent, le code transparent ne doit pas charger d'assemblys à partir d'un tableau d'octets.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, marquez la méthode qui charge l'assembly avec l'attribut <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 La règle se déclenche sur le code suivant car une méthode transparente charge un assembly à partir d'un tableau d'octets.  
  
 [!code-cs[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]