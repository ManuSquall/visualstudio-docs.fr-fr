---
title: "CA2140&#160;: Le code transparent ne doit pas faire r&#233;f&#233;rence &#224; des &#233;l&#233;ments critiques de s&#233;curit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2129"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
  - "CA2140"
helpviewer_keywords: 
  - "CA2129"
  - "CA2140"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA2140&#160;: Le code transparent ne doit pas faire r&#233;f&#233;rence &#224; des &#233;l&#233;ments critiques de s&#233;curit&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Méthode transparente :  
  
-   gère un type d'exception de sécurité critique de sécurité  
  
-   a un paramètre marqué comme type critique de sécurité  
  
-   a un paramètre générique avec des contraintes critiques de sécurité  
  
-   a une variable locale d'un type critique de sécurité  
  
-   référence un type marqué comme critique de sécurité  
  
-   appelle une méthode marquée comme critique de sécurité  
  
-   référence un champ marqué comme critique de sécurité  
  
-   retourne un type marqué comme critique de sécurité  
  
## Description de la règle  
 Un élément de code marqué avec l'attribut <xref:System.Security.SecurityCriticalAttribute> est critique de sécurité.  Une méthode transparente ne peut pas utiliser un élément critique de sécurité.  Si un type transparent essaie d'utiliser un type critique de sécurité un <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , ou <xref:System.FieldAccessException> est déclenché.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, effectuez l'une des opérations suivantes :  
  
-   Marquer l'élément de code qui utilise le code critique de sécurité avec l'attribut <xref:System.Security.SecurityCriticalAttribute>  
  
     \- ou \-  
  
-   Supprimez l'attribut <xref:System.Security.SecurityCriticalAttribute> des éléments de code qui sont marqués comme critiques de sécurité et marquez\-les plutôt avec l'attribut <xref:System.Security.SecuritySafeCriticalAttribute> ou <xref:System.Security.SecurityTransparentAttribute>.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 Dans les exemples suivants, une méthode transparente essaie de référencer une collection générique critique de sécurité, un champ critique de sécurité et une méthode critique de sécurité.  
  
 [!code-cs[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## Voir aussi  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>