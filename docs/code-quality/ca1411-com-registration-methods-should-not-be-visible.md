---
title: "CA1411&#160;: Les m&#233;thodes d&#39;inscription COM ne doivent pas &#234;tre visibles | Microsoft Docs"
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
  - "CA1411"
  - "ComRegistrationMethodsShouldNotBeVisible"
helpviewer_keywords: 
  - "ComRegistrationMethodsShouldNotBeVisible"
  - "CA1411"
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1411&#160;: Les m&#233;thodes d&#39;inscription COM ne doivent pas &#234;tre visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode marquée avec l'attribut <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> est visible de l'extérieur.  
  
## Description de la règle  
 Quand un assembly est enregistré avec le modèle COM \(Component Object Model\), des entrées sont ajoutées au registre pour chaque type COM visible dans l'assembly.  Les méthodes marquées avec les attributs <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> et <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> sont appelées durant les processus d'inscription et d'annulation d'inscription, respectivement, pour exécuter le code utilisateur spécifique à l'inscription et l'annulation d'inscription de ces types.  Ce code ne doit pas être appelé à l'extérieur de ces processus.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, affectez la valeur `private` ou `internal` à l'accessibilité de la méthode \(`Friend` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente deux méthodes qui ne respectent pas la règle.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## Règles connexes  
 [CA1410 : Les méthodes d'inscription COM doivent être mises en correspondance](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registering Assemblies with COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)