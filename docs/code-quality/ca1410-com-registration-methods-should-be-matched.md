---
title: "CA1410&#160;: Les m&#233;thodes d&#39;inscription COM doivent &#234;tre mises en correspondance | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
helpviewer_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1410&#160;: Les m&#233;thodes d&#39;inscription COM doivent &#234;tre mises en correspondance
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type déclare une méthode marquée avec l'attribut <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, mais ne déclare pas une méthode marquée avec l'attribut <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, ou vice\-versa.  
  
## Description de la règle  
 Pour que les clients COM \(Component Object Model\) créent un type [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], le type doit d'abord être enregistré.  Si elle est disponible, une méthode marquée avec l'attribut <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> est appelée pendant le processus d'inscription pour exécuter le code spécifié par l'utilisateur.  Une méthode correspondante marquée avec l'attribut <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> est appelée pendant le processus d'inscription pour inverser les opérations de la méthode d'inscription.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez la méthode d'inscription ou d'annulation d'inscription correspondante.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente un type qui enfreint la règle.  Le code commenté affiche le correctif de la violation.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## Règles connexes  
 [CA1411 : Les méthodes d'inscription COM ne doivent pas être visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registering Assemblies with COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)