---
title: "CA1412&#160;: Marquer les interfaces ComSource comme IDispatch | Microsoft Docs"
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
  - "MarkComSourceInterfacesAsIDispatch"
  - "CA1412"
helpviewer_keywords: 
  - "CA1412"
  - "MarkComSourceInterfacesAsIDispatch"
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1412&#160;: Marquer les interfaces ComSource comme IDispatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type est marqué avec l'attribut <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> et au moins une interface spécifiée n'est pas marquée avec l'attribut <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> ayant la valeur `InterfaceIsDispatch`.  
  
## Description de la règle  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> est utilisé pour identifier les interfaces d'événements qu'une classe expose aux clients COM \(Component Object Model\).  Ces interfaces doivent être exposées comme `InterfaceIsIDispatch` pour permettre aux clients COM Visual Basic 6 de recevoir les notifications d'événement.  Par défaut, si une interface n'est pas marquée avec l'attribut <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, elle est exposée comme une interface double.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez ou modifiez l'attribut <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> afin que sa valeur soit InterfaceIsIDispatch pour toutes les interfaces spécifiées avec l'attribut <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant montre une classe où l'une des interfaces enfreint la règle.  
  
 [!code-cs[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## Règles connexes  
 [CA1408 : Ne pas utiliser le paramètre AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## Voir aussi  
 [How to: Raise Events Handled by a COM Sink](http://msdn.microsoft.com/fr-fr/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)