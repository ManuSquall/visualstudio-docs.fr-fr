---
title: Élément IDSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4489be4ea24382ddaf0fcbe5e824eac3945c9cec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319532"
---
# <a name="idsymbol-element"></a>Élément IDSymbol
Le `IDSymbol` élément contient l’ID de la paire GUID : ID qui représente un menu, un groupe ou une commande. Le GUID est fourni à partir du parent `GuidSymbol` élément. Le `IDSymbol` élément a un `name` attribut qui fournit un nom convivial pour l’ID, qui est contenue dans le `value` attribut.

## <a name="syntax"></a>Syntaxe

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|name|Obligatoire. Nom du symbole de code.|
|par défaut|Obligatoire. Valeur d’ID numérique du symbole de code.|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément GuidSymbol](../extensibility/guidsymbol-element.md)|Contient le GUID de la paire GUID : ID qui représente un menu, un groupe ou une commande. Groupe les éléments `IDSymbol`.|

## <a name="remarks"></a>Notes
 Chaque `IDSymbol` élément dans une donnée `GuidSymbol` élément doit avoir une valeur unique `value`. Toutefois, `IDSymbol` les éléments qui ont des valeurs identiques peuvent exister dans un package, à condition qu’ils disposent des parents différents.

## <a name="see-also"></a>Voir aussi
- [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)