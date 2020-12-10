---
title: Include, élément | Microsoft Docs
description: L’élément Include spécifie un fichier qui peut se trouver dans le chemin include fourni pour insertion dans le fichier actuel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71da1241863e41529af33bdd5e45dcf0a8bfbdb1
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996342"
---
# <a name="include-element"></a>Élément Include
L’élément Include spécifie un fichier qui peut se trouver dans le chemin include fourni pour insertion dans le fichier actuel.  Tous les symboles et types définis feront partie du résultat compilé.

## <a name="syntax"></a>Syntaxe

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|href|Obligatoire. Chemin d’accès au fichier d’en-tête :<br /><br /> href = "stdidcmd. h"|
|Condition|facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Aucun.|Aucun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes, c’est-à-dire des éléments de menu, des menus, des barres d’outils et des zones de liste déroulante, qu’un VSPackage fournit à l’IDE.|

## <a name="example"></a>Exemple

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
