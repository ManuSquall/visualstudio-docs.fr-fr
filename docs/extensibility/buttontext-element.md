---
title: Élément ButtonText (fr) Microsoft Docs
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
ms.openlocfilehash: 59308feea2002a18662a7c04b95a92a920f934c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739910"
---
# <a name="buttontext-element"></a>Élément ButtonText
Ce champ vous permet de spécifier le texte qui apparaît dans différents menus. Par défaut, `ButtonText` l’élément apparaît dans les contrôleurs de menu. L’élément `ButtonText` devient également par défaut si les autres champs de texte sont vides. L’élément `ButtonText` ne peut pas être vide même si les autres champs de texte sont spécifiés.

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
|[Élément cordes](../extensibility/strings-element.md)|Groupes éléments de `ButtonText` texte, tels que et `CommandName`.|

## <a name="text-value"></a>Valeur texte
 La valeur textuelle de l’élément `ButtonText` fournit le texte qui s’affiche pour les éléments de menu, les combos et autres éléments de l’interface utilisateur (interface utilisateur) qui ont du texte visible.

## <a name="see-also"></a>Voir aussi
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
