---
title: Élément IDSymbol | Microsoft Docs
description: 'L’élément IDSymbol contient l’ID de la paire GUID : ID qui représente un menu, un groupe ou une commande.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4feb477f8507bc3fe57e6db355538ab98ceeeaa
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995536"
---
# <a name="idsymbol-element"></a>Élément IDSymbol
L' `IDSymbol` élément contient l’ID de la paire GUID : ID qui représente un menu, un groupe ou une commande. Le GUID provient de l' `GuidSymbol` élément parent. L' `IDSymbol` élément a un `name` attribut qui fournit un nom convivial pour l’ID, qui est contenu dans l' `value` attribut.

## <a name="syntax"></a>Syntaxe

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|name|Obligatoire. Nom du symbole d’ID.|
|value|Obligatoire. Valeur d’ID numérique du symbole d’ID.|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément GuidSymbol](../extensibility/guidsymbol-element.md)|Contient le GUID de la paire GUID : ID qui représente un menu, un groupe ou une commande. Groupe les éléments `IDSymbol`.|

## <a name="remarks"></a>Notes
 Chaque `IDSymbol` élément d’un `GuidSymbol` élément donné doit avoir un unique `value` . Toutefois, les `IDSymbol` éléments qui ont des valeurs identiques peuvent exister dans un package, à condition qu’ils aient des parents différents.

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
