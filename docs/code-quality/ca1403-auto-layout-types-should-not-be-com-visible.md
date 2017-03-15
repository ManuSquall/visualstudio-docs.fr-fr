---
title: "CA1403&#160;: Les types Structurer automatiquement ne doivent pas &#234;tre visibles par COM | Microsoft Docs"
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
  - "AutoLayoutTypesShouldNotBeComVisible"
  - "CA1403"
helpviewer_keywords: 
  - "CA1403"
  - "AutoLayoutTypesShouldNotBeComVisible"
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1403&#160;: Les types Structurer automatiquement ne doivent pas &#234;tre visibles par COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type de valeur COM \(Component Object Model\) visible est marqué avec l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> défini sur la valeur <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
## Description de la règle  
 Les types de disposition <xref:System.Runtime.InteropServices.LayoutKind> sont gérés par le Common Language Runtime.  La disposition de ces types peut varier suivant les versions du .NET Framework, ce qui bloque les clients COM qui attendent une disposition spécifique.  Notez que si l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> n'est pas spécifié, les compilateurs C\#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] et C\+\+ spécifient la disposition <xref:System.Runtime.InteropServices.LayoutKind> pour les types valeur.  
  
 Sauf s'ils sont marqués autrement, tous les types publics et non génériques sont visibles dans COM ; tous les types non publics et génériques ne sont pas visibles dans COM.  Toutefois, pour limiter les faux positifs, cette règle requiert que la visibilité COM du type soit déclarée explicitement ; l'assembly contenant doit être marqué avec <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ayant la valeur `false` et le type doit être marqué avec <xref:System.Runtime.InteropServices.ComVisibleAttribute> ayant la valeur `true`.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez la valeur de l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> par <xref:System.Runtime.InteropServices.LayoutKind> ou <xref:System.Runtime.InteropServices.LayoutKind>, ou faites en sorte que le type soit invisible dans COM.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente un type qui viole la règle et un autre qui satisfait la règle.  
  
 [!CODE [FxCop.Interoperability.AutoLayout#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout#1)]  
  
## Règles connexes  
 [CA1408 : Ne pas utiliser le paramètre AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## Voir aussi  
 [Introducing the Class Interface](http://msdn.microsoft.com/fr-fr/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)