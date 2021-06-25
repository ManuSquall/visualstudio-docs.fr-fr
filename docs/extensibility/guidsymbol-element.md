---
title: Élément GuidSymbol | Microsoft Docs
description: 'L’élément GuidSymbol contient le GUID de la paire GUID : ID qui représente un menu, un groupe ou une commande.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c30c7a48b03b5deed3267e106e926d3cb5114c1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902759"
---
# <a name="guidsymbol-element"></a>Élément GuidSymbol
L' `GuidSymbol` élément contient le GUID de la paire GUID : ID qui représente un menu, un groupe ou une commande. L’ID provient d’un `IDSymbol` élément dans l' `GuidSymbol` élément. L' `GuidSymbol` élément a un `name` attribut qui fournit un nom convivial pour le GUID, qui est contenu dans l' `value` attribut.

## <a name="syntax"></a>Syntaxe

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|name|Obligatoire. Nom du symbole GUID.|
|valeur|Obligatoire. GUID du symbole GUID.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément IDSymbol](../extensibility/idsymbol-element.md)|Contient l’ID de la paire GUID : ID qui représente un menu, un groupe ou une commande.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Symbols](../extensibility/symbols-element.md)|Regroupe les `GuidSymbol` éléments dans un fichier *. vsct* .|

## <a name="remarks"></a>Remarques
 En règle générale, un fichier *. vsct* contient trois `GuidSymbol` éléments dans sa `Symbols` section, l’un pour le package lui-même, l’autre pour le jeu de commandes (la collection de menus, les groupes et les commandes que le package rend disponibles) et l’autre pour les bitmaps qui fournissent des icônes pour les boutons et autres composants visuels. Chaque `IDSymbol` élément d’un `GuidSymbol` élément donné doit avoir un unique `value` . Toutefois, les `IDSymbol` éléments qui ont des valeurs identiques peuvent exister dans un package, à condition qu’ils aient des parents différents.

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
