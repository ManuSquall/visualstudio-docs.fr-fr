---
title: CommandName, élément | Microsoft Docs
description: L’élément CommandName spécifie le texte qui apparaît dans la catégorie clavier dans la boîte de dialogue Options et dans la liste commandes de la boîte de dialogue Personnaliser.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandName element (VSCT XML schema)
- VSCT XML schema elements, CommandName
ms.assetid: a338b767-aa7e-4536-9908-e19a50ab60ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ba74c0a61ddf01407f2af6ebb8053e2f1e4fe6ac
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089626"
---
# <a name="commandname-element"></a>Élément CommandName
L' `CommandName` élément spécifie le texte qui apparaît dans la catégorie clavier de la boîte de dialogue **options** et dans la liste **commandes** de la boîte de dialogue **personnaliser** .

## <a name="syntax"></a>Syntaxe

```
<CommandName>MyCommand</CommandName>
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

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
