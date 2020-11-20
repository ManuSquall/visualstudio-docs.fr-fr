---
title: ButtonText, élément | Microsoft Docs
description: L’élément ButtonText vous permet de spécifier le texte qui apparaît dans différents menus. L’élément ButtonText ne peut pas être vide, même si d’autres champs de texte sont spécifiés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2db20bb3298a7b849e8bc4a261987c5314a29841
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974466"
---
# <a name="buttontext-element"></a>Élément ButtonText
Ce champ vous permet de spécifier le texte qui apparaît dans différents menus. Par défaut, l' `ButtonText` élément apparaît dans les contrôleurs de menu. L' `ButtonText` élément devient également la valeur par défaut si les autres champs de texte sont vides. L' `ButtonText` élément ne peut pas être vide même si les autres champs de texte sont spécifiés.

## <a name="syntax"></a>Syntaxe

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Strings](../extensibility/strings-element.md)|Groupe des éléments de texte, tels que `ButtonText` et `CommandName` .|

## <a name="text-value"></a>Valeur texte
 La valeur texte de l' `ButtonText` élément fournit le texte affiché pour les éléments de menu, les combos et d’autres éléments de l’interface utilisateur qui ont du texte visible.

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
