---
title: "&#201;l&#233;ment de bitmap | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, les Bitmaps"
  - "Bitmaps, élément (schéma XML de VSCT)"
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# &#201;l&#233;ment de bitmap
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit une image bitmap. La bitmap est chargée à partir d'une ressource ou d'un fichier.  
  
## Syntaxe  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|GUID|Obligatoire. GUID de l'identificateur de commande\/ID GUID.<br /><br /> L'attribut de guid pour une image bitmap n'est pas associé à un VSPackage ou autre groupe de commandes.  Il doit être unique dans la définition de bitmap et ne doit pas être utilisé à d'autres fins.|  
|resID|ID de l'identificateur de commande\/ID GUID. Le resID ou l'attribut href est nécessaire.<br /><br /> L'attribut resID est un ID de ressource d'entier qui détermine la bande bitmap qui doit être chargé au cours de la fusion des tables de commande.  Lorsque la table commandes est chargée, les bitmaps spécifiées par l'ID de ressource est chargés à partir de la ressource du même module.|  
|usedList|Obligatoire si l'attribut resID est présent. Sélectionne les images disponibles dans la bande de la bitmap.|  
|href|Chemin d'accès à la bitmap. Le resID ou l'attribut href est nécessaire.<br /><br /> Le chemin d'accès include est recherchés dans le fichier image indiqué, ce qui est incorporé dans le fichier binaire qui en résulte.  Lors de la fusion de la table commandes, l'image est copiée et aucune recherche de ressources supplémentaires ou la charge est requise.  Si l'attribut usedList n'est pas présent, toutes les images dans la bande sont disponibles. **Note:**  Les images peuvent être fournies dans un des formats qui comprennent .bmp, .png et .gif.  Les versions antérieures du compilateur ne prenait pas en charge les images bitmap de 32 bits qui avaient des informations alpha pour la transparence partielle. Pour ces versions de la solution de contournement consiste à utiliser le format .png.|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments de la Bitmap.|  
  
## Exemple  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/>  
```  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)