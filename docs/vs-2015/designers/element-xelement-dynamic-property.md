---
title: Element (propriété dynamique XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c6171a5dedfd6985a6f54e748011bf86e03f4d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664652"
---
# <a name="element-xelement-dynamic-property"></a>Element (propriété dynamique XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtient un indexeur utilisé pour récupérer l'instance d'élément enfant qui correspond au nom développé spécifié.

## <a name="syntax"></a>Syntaxe

```
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour
 Indexeur de type `XElement Item(String expandedName)`. Cet indexeur prend un paramètre de nom développé et retourne l'objet <xref:System.Xml.Linq.XElement> correspondant ou `null` s'il n'existe aucun élément avec le nom spécifié.

## <a name="remarks"></a>Notes
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Element%2A> de la classe <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.

## <a name="see-also"></a>Voir aussi
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>[Éléments](../designers/elements-xelement-dynamic-property.md) de [propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)
