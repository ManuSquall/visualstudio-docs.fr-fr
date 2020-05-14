---
title: Élément GuidSymbol ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711129"
---
# <a name="guidsymbol-element"></a>Élément GuidSymbol
L’élément `GuidSymbol` contient le GUID de la paire GUID:ID qui représente un menu, un groupe ou une commande. L’ID provient `IDSymbol` d’un élément de l’élément. `GuidSymbol` L’élément `GuidSymbol` `name` a un attribut qui fournit un nom amical `value` pour le GUID, qui est contenu dans l’attribut.

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
|value|Obligatoire. GUID du symbole GUID.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément IDSymbol](../extensibility/idsymbol-element.md)|Contient l’ID de la paire GUID:ID qui représente un menu, un groupe ou une commande.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément symbole](../extensibility/symbols-element.md)|Regroupez les `GuidSymbol` éléments d’un fichier *.vsct.*|

## <a name="remarks"></a>Notes
 Typiquement, un fichier *.vsct* contient trois `GuidSymbol` éléments dans sa `Symbols` section, un pour le paquet lui-même, un pour l’ensemble de commande (la collection de menus, de groupes et de commandes que le paquet met à disposition), et un pour les bitmaps qui fournissent des icônes pour les boutons et autres composants visuels. Chaque `IDSymbol` élément d’un élément `GuidSymbol` `value`donné doit avoir un caractère unique. Cependant, `IDSymbol` les éléments qui ont des valeurs identiques peuvent exister dans un paquet tant qu’ils ont des parents différents.

## <a name="see-also"></a>Voir aussi
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
