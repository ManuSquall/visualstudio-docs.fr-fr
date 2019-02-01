---
title: Value (propriété dynamique XAttribute) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2b83e4a208553b0ad732cfe927aec02b47e389dd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757540"
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
