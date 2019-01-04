---
title: Élément bitmap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dbdd61e22a392309c45005c0e183704c6b84040c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879369"
---
# <a name="bitmap-element"></a>Élément de bitmap
Définit une image bitmap. La bitmap est chargée à partir d’une ressource ou d’un fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire. GUID de l’identificateur de commande/ID GUID.<br /><br /> L’attribut de guid pour une image bitmap n’est pas associé à n’importe quel package Visual Studio ou l’autre groupe de commandes.  Il doit être unique à la définition de bitmap et ne doit pas être utilisé à d’autres fins.|  
|resID|ID de l’identificateur de commande/ID GUID. Le resID ou l’attribut href est requis.<br /><br /> L’attribut resID est un ID de ressource d’entier qui détermine la bande de bitmaps qui doit être chargé pendant la fusion des tables de commande.  Lorsque la table de commande est chargée, les bitmaps spécifiées par l’ID de ressource sera chargées à partir de la ressource du même module.|  
|usedList|Obligatoire si l’attribut resID n’est présent. Sélectionne les images disponibles dans la bande de bitmaps.|  
|href|Chemin d’accès à l’image bitmap. Le resID ou l’attribut href est requis.<br /><br /> Le chemin d’accès include est recherchés dans le fichier image indiqué, qui est incorporé dans le fichier binaire qui en résulte.  Pendant la fusion de table de commande, l’image est copiée et aucune recherche de ressources supplémentaires ou de la charge n’est nécessaire.  Si l’attribut usedList n’est pas présent, toutes les images dans la bande sont disponibles. **Remarque :**  Les images peuvent être fournies dans un des formats qui incluent *.bmp*, *.png*, et *.gif*.  Les versions antérieures du compilateur ne prenait pas en charge les images bitmap 32 bits qui avait des informations alpha pour la transparence partielle. La solution de contournement pour ces versions consiste à utiliser le *.png* format.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments de la Bitmap.|  
  
## <a name="example"></a>Exemple  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)