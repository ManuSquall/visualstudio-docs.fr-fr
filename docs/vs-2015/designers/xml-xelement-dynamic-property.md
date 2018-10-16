---
title: Xml (propriété dynamique XElement) | Microsoft Docs
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
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6daf831030fd02f3aa1e3a4844a42ba60bf0574c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175810"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (propriété dynamique XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtient le contenu XML sans mise en forme de l'élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 <xref:System.String> qui représente le contenu XML sans mise en forme de l'élément.  
  
## <a name="remarks"></a>Notes  
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> de la classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, avec le paramètre `SaveOptions` défini à la valeur <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valeur](../designers/value-xelement-dynamic-property.md)



