---
title: Élément bitmap | Microsoft Docs
description: L’élément bitmap définit une image bitmap. L’image bitmap est chargée à partir d’une ressource ou d’un fichier. Cet article contient un exemple.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd30cb2d09d042e70b5fc142ac220f2356962146
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974586"
---
# <a name="bitmap-element"></a>Élément bitmap
Définit une image bitmap. L’image bitmap est chargée à partir d’une ressource ou d’un fichier.

## <a name="syntax"></a>Syntaxe

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID de l’identificateur de la commande GUID/ID.<br /><br /> L’attribut Guid d’une image bitmap n’est associé à aucun VSPackage ou autre groupe de commandes.  Elle doit être unique pour la définition de la bitmap et ne doit pas être utilisée à d’autres fins.|
|resID|ID de l’identificateur de la commande GUID/ID. L’attribut resID ou href est requis.<br /><br /> L’attribut resID est un ID de ressource entier qui détermine la bande de bitmaps à charger lors de la fusion de la table de commandes.  Lorsque la table de commandes est chargée, les bitmaps spécifiés par l’ID de ressource sont chargés à partir de la ressource du même module.|
|usedList|Obligatoire si l’attribut resID est présent. Sélectionne les images disponibles dans la bande bitmap.|
|href|Chemin d’accès à l’image bitmap. L’attribut resID ou href est requis.<br /><br /> Le chemin d’accès include est recherché dans le fichier image indiqué, qui est incorporé dans le fichier binaire résultant.  Pendant la fusion de la table de commandes, l’image est copiée et aucune recherche ou charge de ressources supplémentaire n’est requise.  Si l’attribut usedList n’est pas présent, toutes les images de la bande sont disponibles. **Remarque :**  Les images peuvent être fournies dans l’un des formats suivants : *. bmp*, *. png* et *. gif*.  Les versions antérieures du compilateur ne prenaient pas en charge les images bitmap 32 bits qui avaient des informations alpha pour la transparence partielle. La solution de contournement pour ces versions consiste à utiliser le format *. png* .|
|Condition|facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments bitmap.|

## <a name="example"></a>Exemple

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
