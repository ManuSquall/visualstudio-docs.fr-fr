---
title: Xml (propriété dynamique XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c794d79d62fc580001efc5cf16993d4ac5fef48b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663846"
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
 [Valeur](../designers/value-xelement-dynamic-property.md) des [propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)
