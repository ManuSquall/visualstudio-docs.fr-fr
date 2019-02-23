---
title: Élément ButtonText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 519ba206b334ef9c955245c152fb14663366472b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698831"
---
# <a name="buttontext-element"></a>Élément ButtonText
Ce champ vous permet de spécifier le texte qui apparaît dans différents menus. Par défaut, le `ButtonText` élément apparaît dans les contrôleurs de menu. Le `ButtonText` élément devient également la valeur par défaut si les autres champs de texte sont vides. Le `ButtonText` élément ne peut pas être vide, même si les autres champs de texte sont spécifiées.

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
|[Élément Strings](../extensibility/strings-element.md)|Regroupe les éléments de texte, tel que `ButtonText` et `CommandName`.|

## <a name="text-value"></a>Valeur texte
 La valeur de texte de la `ButtonText` élément fournit le texte qui est affiché pour les éléments de menu, combinés et autres éléments d’interface (UI) dont le texte visible.

## <a name="see-also"></a>Voir aussi
- [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)