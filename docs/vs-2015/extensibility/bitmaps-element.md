---
title: Élément bitmaps | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb0e241b3767e8c730438ca29b6874d1a385ef2b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508805"
---
# <a name="bitmaps-element"></a>Élément Bitmaps
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Bitmaps élément](https://docs.microsoft.com/visualstudio/extensibility/bitmaps-element).  
  
Groupes [élément de Bitmap](../extensibility/bitmap-element.md) éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Bitmaps>  
  <Bitmap>... </Bitmap>  
  <Bitmap>... </Bitmap>  
</Bitmaps>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments de la Bitmap.|  
|[Élément Bitmap](../extensibility/bitmap-element.md)|Définit une image bitmap.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Commands](../extensibility/commands-element.md)|Représente la collection de commandes sur la barre d’outils de VSPackage.|  
  
## <a name="example"></a>Exemple  
  
```  
<Bitmaps>  
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
    usedList="1, 2, 3, 4"/>  
</Bitmaps>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment VSPackages ajoute des éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)

