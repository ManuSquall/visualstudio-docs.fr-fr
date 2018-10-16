---
title: Value (propriété dynamique XAttribute) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd9ea1fa163980a39bcd9981b9e1d757d72fcb6a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229149"
---
# <a name="value-xattribute-dynamic-property"></a>Value (propriété dynamique XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtient ou définit la valeur de l'attribut XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
attrib.Value   
```  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 <xref:System.String> contenant la valeur de cet attribut.  
  
## <a name="exceptions"></a>Exceptions  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|Lors de la définition, `value` a la valeur `null`.|  
  
## <a name="remarks"></a>Notes  
 Cette propriété est équivalente à la propriété <xref:System.Xml.Linq.XAttribute.Value%2A> de la classe <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, mais cette propriété dynamique prend également en charge les notifications de changement.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Propriétés dynamiques de la classe XAttribute](../designers/xattribute-class-dynamic-properties.md)   
 [Attribut](../designers/attribute-xelement-dynamic-property.md)



