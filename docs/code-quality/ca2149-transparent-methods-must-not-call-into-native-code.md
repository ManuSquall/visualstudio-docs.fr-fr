---
title: "CA2149&#160;: Les m&#233;thodes transparentes ne doivent pas appeler du code natif | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2149"
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2149&#160;: Les m&#233;thodes transparentes ne doivent pas appeler du code natif
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallNativeCode|  
|CheckId|CA2149|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode appelle une fonction native via un stub de méthode tel que P\/Invoke.  
  
## Description de la règle  
 Cette règle se déclenche sur toute méthode transparente qui appelle directement en code natif \(par exemple, via un appel P\/Invoke\).  Les violations de cette règle provoquent une <xref:System.MethodAccessException> dans le modèle de transparence de niveau 2, et une demande complète pour <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> dans le modèle de transparence de niveau 1.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, marquez la méthode qui appelle le code natif avec l'attribut <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 [!CODE [FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode#1)]