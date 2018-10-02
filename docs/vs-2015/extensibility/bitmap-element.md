---
title: Élément bitmap | Microsoft Docs
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
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efcf92479b26e25b1eab485851a849ab083cc54c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494925"
---
# <a name="bitmap-element"></a>Élément Bitmap
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [élément de Bitmap](https://docs.microsoft.com/visualstudio/extensibility/bitmap-element).  
  
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
|href|Chemin d’accès à l’image bitmap. Le resID ou l’attribut href est requis.<br /><br /> Le chemin d’accès include est recherchés dans le fichier image indiqué, qui est incorporé dans le fichier binaire qui en résulte.  Pendant la fusion de table de commande, l’image est copiée et aucune recherche de ressources supplémentaires ou de la charge n’est nécessaire.  Si l’attribut usedList n’est pas présent, toutes les images dans la bande sont disponibles. **Remarque :** Images peuvent être fournies dans un des formats qui incluent .bmp, .png et .gif.  Les versions antérieures du compilateur ne prenait pas en charge les images bitmap 32 bits qui avait des informations alpha pour la transparence partielle. La solution de contournement pour ces versions consiste à utiliser le format .png.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments de la Bitmap.|  
  
## <a name="example"></a>Exemple  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

