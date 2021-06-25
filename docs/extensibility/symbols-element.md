---
title: Symbols, élément | Microsoft Docs
description: L’élément Symbols définit les GUID et les ID utilisés par d’autres éléments VSCT. Cet article contient un exemple.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b593f353714f2fbb6f5b726fa2bbc0da449043ea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901732"
---
# <a name="symbols-element"></a>Élément Symbols
Définit les GUID et les ID utilisés par d’autres éléments VSCT. Pour le code non managé, ces informations proviennent généralement des fichiers d’en-tête spécifiés par l' [élément extern](../extensibility/extern-element.md). Le code managé utilise les éléments enfants de l’élément Symbols pour définir ces informations.

 Si vous créez un fichier. vsct à partir d’un fichier. directeur de la génération existante, les symboles sont générés en tant qu’enfants de l’élément Symbols. Pour plus d’informations, consultez [Comment : créer un. Fichier vsct à partir d’un existant. Fichier de directeur technique](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 L’élément Symbols ne doit pas être confondu avec l' [élément define](../extensibility/define-element.md), qui définit des paires nom-valeur pour une utilisation par le préprocesseur.

## <a name="syntax"></a>Syntaxe

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|Aucune||

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|GuidSymbol|Définit un symbole GUID. GuidSymbol a deux attributs obligatoires : Name et value. Le nom est le nom du symbole et la valeur est la valeur du GUID sous la forme d’une chaîne.<br /><br /> Par exemple :\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|Définit un symbole. IDSymbol a deux attributs obligatoires : Name et value. Le nom est le nom du symbole et la valeur est la valeur du symbole sous la forme d’une chaîne.<br /><br /> Par exemple :\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Élément racine du fichier. vsct.|

## <a name="example"></a>Exemple

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>Voir aussi
- [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
