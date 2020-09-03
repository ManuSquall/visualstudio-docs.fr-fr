---
title: Include, élément | Microsoft Docs
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
ms.openlocfilehash: 7ea89185d28be2816a690d867dbb3eccbb739e04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710358"
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
