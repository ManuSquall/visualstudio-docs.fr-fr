---
title: "CA1412 : Marquer les Interfaces ComSource comme IDispatch | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8a53053588670fef616f4df7633b3a25fb45712
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412 : Marquer les interfaces ComSource comme IDispatch
|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type est marqué avec la <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attribut et au moins une interface spécifiée n’est pas marqué avec le <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attribut défini sur le `InterfaceIsDispatch` valeur.  
  
## <a name="rule-description"></a>Description de la règle  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>Permet d’identifier les interfaces d’événements qu’une classe expose aux clients de modèle COM (Component Object). Ces interfaces doivent être exposées en tant que `InterfaceIsIDispatch` par les clients COM Visual Basic 6 recevoir des notifications d’événements. Par défaut, si une interface n’est pas marquée avec le <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attribut, elle est exposée comme une interface double.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez ou modifiez la <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attribut afin que sa valeur soit InterfaceIsIDispatch pour toutes les interfaces qui sont spécifiées avec la <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attribut.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une classe où une des interfaces enfreint la règle.  
  
 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1408 : N’utilisez pas le paramètre AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : déclencher des événements gérés par un récepteur COM](http://msdn.microsoft.com/en-us/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [Interopération avec du code non managé](/dotnet/framework/interop/index)