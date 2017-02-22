---
title: "CA2145&#160;: Les m&#233;thodes transparentes ne doivent pas &#234;tre d&#233;cor&#233;es avec SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2145"
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2145&#160;: Les m&#233;thodes transparentes ne doivent pas &#234;tre d&#233;cor&#233;es avec SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode transparente, une méthode marquée avec la méthode <xref:System.Security.SecuritySafeCriticalAttribute>, ou un type qui contient une méthode est marquée avec l'attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.  
  
## Description de la règle  
 Les méthodes décorées avec l'attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> ont un LinkDemand implicite placé sur toute méthode qui l'appelle.  Ce LinkDemand requiert que le code appelant soit critique de sécurité.  Le marquage de la méthode qui utilise SuppressUnmanagedCodeSecurity avec l'attribut <xref:System.Security.SecurityCriticalAttribute> rend cette spécification plus évidente pour les appelants de la méthode.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, marquez la méthode ou le type avec l'attribut <xref:System.Security.SecurityCriticalAttribute>.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
### Code  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### Commentaires