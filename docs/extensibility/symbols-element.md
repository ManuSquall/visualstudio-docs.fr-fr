---
title: Élément symboles Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699347"
---
# <a name="symbols-element"></a>Élément Symbols
Définit les GUIDs et les IED qui sont utilisés par d’autres éléments VSCT. Pour le code non menté, ces informations proviennent généralement des fichiers d’en-tête qui sont spécifiés par [Extern Element](../extensibility/extern-element.md). Le code géré utilise les éléments enfants de l’élément Symboles pour définir ces informations.

 Si vous créez un fichier .vsct à partir d’un fichier .cto existant, les symboles seront générés en tant qu’enfants de l’élément Symboles. Pour plus d’informations, voir [Comment : Créer un . Fichier Vsct à partir d’un existant . Fichier Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 L’élément Symboles ne doit pas être confondu avec [l’élément défini](../extensibility/define-element.md), qui définit les paires de valeur nominale pour une utilisation par le préprocesseur.

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
|None||

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|GuidSymbol|Définit un symbole GUID. GuidSymbol a deux attributs requis : le nom et la valeur. Le nom est le nom du symbole, et la valeur est la valeur de la GUID comme une chaîne.<br /><br /> Par exemple\<: GuidSymbol nameMD "guidVsPackage1Pkg" valeur "c5f54698-101a-4846-84d3-dc748f9cd848" />|
|IDSymbol (EN)|Définit un symbole. IDSymbol a deux attributs requis : le nom et la valeur. Le nom est le nom du symbole, et la valeur est la valeur du symbole comme une chaîne.<br /><br /> Par exemple\<: IDSymbol nameMD "MyMenuGroup" value "0x1020" />|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|L’élément racine du fichier .vsct.|

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
