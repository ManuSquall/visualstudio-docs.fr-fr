---
title: Value (propriété dynamique XAttribute) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: af8f122bfbf2ce37b161afb5f0665a9677ef2f3b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506661"
---
# <a name="value-xattribute-dynamic-property"></a>Value (propriété dynamique XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Value (propriété dynamique XAttribute)](https://docs.microsoft.com/visualstudio/designers/value-xattribute-dynamic-property).  
  
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



