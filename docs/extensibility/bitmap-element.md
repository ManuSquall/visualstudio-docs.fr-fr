---
title: Élément Bitmap - France Microsoft Docs
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
ms.openlocfilehash: 2d663351aad7d381dd5bfe4cbaa0a263cc70b821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740001"
---
# <a name="bitmap-element"></a>Élément Bitmap
Définit un bitmap. Le bitmap est chargé à partir d’une ressource ou d’un fichier.

## <a name="syntax"></a>Syntaxe

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID de l’identifiant de commande GUID/ID.<br /><br /> L’attribut guid pour un bitmap n’est pas associé à un VSPackage ou un autre groupe de commande.  Il devrait être unique à la définition de bitmap et ne doit pas être utilisé à d’autres fins.|
|resID (resID)|ID de l’identifiant de commande GUID/ID. Soit le resID ou l’attribut href est nécessaire.<br /><br /> L’attribut resID est une pièce d’identité de ressource integer qui détermine la bande de bitmap qui doit être chargée pendant la fusion de table de commande.  Lorsque le tableau de commande est chargé, les bitmaps spécifiés par l’ID de ressource seront chargés à partir de la ressource du même module.|
|usedList (en)|Nécessaire si l’attribut resID est présent. Sélectionne les images disponibles dans la bande de bitmap.|
|href|Chemin vers la bitmap. Soit le resID ou l’attribut href est nécessaire.<br /><br /> Le chemin inclus est recherché pour le fichier d’image indiqué, qui est intégré dans le binaire résultant.  Pendant la fusion du tableau de commande, l’image est copiée et aucune recherche ou charge supplémentaire de ressource n’est exigée.  Si l’attribut UsedList n’est pas présent, toutes les images de la bande sont disponibles. **Note:**  Les images peuvent être fournies dans l’un des plusieurs formats qui comprennent *.bmp*, *.png*, et *.gif*.  Les versions antérieures du compilateur ne supportaient pas les images de bits 32 bits qui avaient des informations alpha pour une transparence partielle. La solution de contournement pour ces versions est d’utiliser le format *.png.*|
|Condition|facultatif. Voir [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Bitmaps](../extensibility/bitmaps-element.md)|Groupes Bitmap éléments.|

## <a name="example"></a>Exemple

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Voir aussi
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
