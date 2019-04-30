---
title: Élément Icon | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a53e7971ac54af439a02d765fb392157d4a5321
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911197"
---
# <a name="icon-element"></a>Élément Icon
L’attribut guid de la balise de l’icône est le guid d’une image bitmap définis. Le `id` attribut sélectionne l’emplacement de la bande de bitmaps. Cet élément est facultatif. Si cet élément n’est pas inclus la valeur de **guidOfficeIcon:msotcidNoIcon** est implicite.

## <a name="syntax"></a>Syntaxe

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. Le guid d’une image bitmap définis.|
|ID|Obligatoire. Sélectionne l’emplacement de la bande de bitmaps.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Aucun.|Aucun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Buttons](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Voir aussi
- [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)