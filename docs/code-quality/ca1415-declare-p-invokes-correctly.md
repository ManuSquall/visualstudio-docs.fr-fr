---
title: "CA1415&#160;: D&#233;clarer correctement les m&#233;thodes P/Invoke | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
helpviewer_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1415&#160;: D&#233;clarer correctement les m&#233;thodes P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Sans rupture \- Si P\/Invoke qui déclare le paramètre n'est pas visible à l'extérieur de l'assembly.  Avec rupture \- si le P\/Invoke qui déclare le paramètre est visible à l'extérieur de l'assembly.|  
  
## Cause  
 Une méthode d'appel de code non managé est déclarée de manière incorrecte.  
  
## Description de la règle  
 Une méthode d'appel de code non managé accède à un code non managé et est définie à l'aide du mot clé `Declare` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou de l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  Cette règle recherche actuellement des déclarations de méthode d'appel de code non managé qui ciblent des fonctions Win32 présentant un pointeur vers un paramètre de structure OVERLAPPED, et le paramètre managé correspondant n'est pas un pointeur vers une structure <xref:System.Threading.NativeOverlapped?displayProperty=fullName>.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, déclarez correctement la méthode d'appel de code non managé.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente des méthodes d'appel de code non managé qui enfreignent et respectent la règle.  
  
 [!CODE [FxCop.Interoperability.DeclarePInvokes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes#1)]  
  
## Voir aussi  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)