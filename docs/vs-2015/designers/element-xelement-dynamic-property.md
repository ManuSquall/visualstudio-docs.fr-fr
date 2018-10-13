---
title: Element (propriété dynamique XElement) | Microsoft Docs
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
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 879e5afb112df1f4c82cec150175b24456c1b0a4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256150"
---
# <a name="element-xelement-dynamic-property"></a>Element (propriété dynamique XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtient un indexeur utilisé pour récupérer l’instance d’élément enfant qui correspond au nom développé spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Indexeur de type `XElement Item(String expandedName)`. Cet indexeur prend un paramètre de nom développé et retourne l’objet <xref:System.Xml.Linq.XElement> correspondant ou `null` s’il n’existe aucun élément avec le nom spécifié.  
  
## <a name="remarks"></a>Notes  
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Element%2A> de la classe <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Élements](../designers/elements-xelement-dynamic-property.md)



