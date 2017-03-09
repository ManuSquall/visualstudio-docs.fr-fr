---
title: "CA1408&#160;: Ne pas utiliser le param&#232;tre AutoDual ClassInterfaceType | Microsoft Docs"
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
  - "DoNotUseAutoDualClassInterfaceType"
  - "CA1408"
helpviewer_keywords: 
  - "CA1408"
  - "DoNotUseAutoDualClassInterfaceType"
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1408&#160;: Ne pas utiliser le param&#232;tre AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type COM \(Component Object Model\) visible est marqué avec l'attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> défini sur la valeur `AutoDual` de <xref:System.Runtime.InteropServices.ClassInterfaceType>.  
  
## Description de la règle  
 Les types qui utilisent une interface double permettent aux clients de se lier à une disposition d'interface spécifique.  Les modifications apportées à une version future de la disposition du type ou des types de base bloquent les clients COM qui se lient à l'interface.  Par défaut, si l'attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> n'est pas spécifié, une interface de répartition uniquement est utilisée.  
  
 Sauf s'ils sont marqués autrement, tous les types publics et non génériques sont visibles dans COM ; tous les types non publics et génériques ne sont pas visibles dans COM.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez la valeur de l'attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> par la valeur `None` de <xref:System.Runtime.InteropServices.ClassInterfaceType> et définissez explicitement l'interface.  
  
## Quand supprimer les avertissements  
 Ne supprimez pas d'avertissement de cette règle sauf s'il est certain que la disposition du type et de ses types de base ne change pas dans une version future.  
  
## Exemple  
 L'exemple suivant présente une classe qui ne respecte pas la règle et une nouvelle déclaration de la classe pour utiliser une interface explicite.  
  
 [!code-cs[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## Règles connexes  
 [CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412 : Marquer les interfaces ComSource comme IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## Voir aussi  
 [Introducing the Class Interface](http://msdn.microsoft.com/fr-fr/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)