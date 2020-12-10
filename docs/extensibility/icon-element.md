---
title: Icon, élément | Microsoft Docs
description: En savoir plus sur l’élément Icon, qui représente les icônes utilisées dans les extensions de l’IDE Visual Studio, qui incluent des attributs pour l’image bitmap utilisée et l’emplacement dans la bande bitmap.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ed5a4f64a2c80cfdc61b37a6a8bac72adc97a33
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993599"
---
# <a name="icon-element"></a>Icon, élément
L’attribut Guid de la balise Icon est le GUID d’une image bitmap définie. L' `id` attribut sélectionne l’emplacement dans la bande bitmap. Cet élément est facultatif. Si cet élément n’est pas inclus, la valeur de **guidOfficeIcon : msotcidNoIcon** sera implicite.

## <a name="syntax"></a>Syntaxe

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID d’une image bitmap définie.|
|id|Obligatoire. Sélectionne l’emplacement dans la bande bitmap.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Aucun.|Aucun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Buttons, élément](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
