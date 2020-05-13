---
title: Inclure l’élément Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710358"
---
# <a name="include-element"></a>Inclure l’élément
L’élément Inclure spécifie un fichier qui peut être situé sur le chemin fourni inclure le chemin d’insertion dans le fichier actuel.  Tous les symboles et types définis feront partie du résultat compilé.

## <a name="syntax"></a>Syntaxe

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|href|Obligatoire. Le chemin vers le fichier d’en-tête:<br /><br /> href "stdidcmd.h"|
|Condition|facultatif. Voir [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Aucun.|Aucun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes — c’est-à-dire les éléments de menu, les menus, les barres d’outils et les boîtes combo — qu’un VSPackage fournit à l’IDE.|

## <a name="example"></a>Exemple

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Voir aussi
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
