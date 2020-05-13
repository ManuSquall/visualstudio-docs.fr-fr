---
title: Élément IDSymbol ( Microsoft Docs
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
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710373"
---
# <a name="idsymbol-element"></a>Élément IDSymbol
L’élément `IDSymbol` contient l’ID de la paire GUID:ID qui représente un menu, un groupe ou une commande. Le GUID provient `GuidSymbol` de l’élément parent. L’élément `IDSymbol` `name` a un attribut qui fournit un nom amical `value` pour l’ID, qui est contenu dans l’attribut.

## <a name="syntax"></a>Syntaxe

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|name|Obligatoire. Nom du symbole d’identification.|
|value|Obligatoire. Valeur d’identification numérique du symbole d’identification.|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément GuidSymbol](../extensibility/guidsymbol-element.md)|Contient le GUID de la paire GUID:ID qui représente un menu, un groupe ou une commande. Groupe les éléments `IDSymbol`.|

## <a name="remarks"></a>Notes
 Chaque `IDSymbol` élément d’un élément `GuidSymbol` `value`donné doit avoir un caractère unique. Cependant, `IDSymbol` les éléments qui ont des valeurs identiques peuvent exister dans un paquet tant qu’ils ont des parents différents.

## <a name="see-also"></a>Voir aussi
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
