---
title: Élément parent (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702216"
---
# <a name="parent-element"></a>Élément parent
Le parent d’un bouton ou d’une boîte combo ne peut être qu’un groupe. Le parent d’un menu ou d’un groupe peut être n’importe quel autre menu ou groupe. Dans un [élément CommandPlacement,](../extensibility/commandplacement-element.md)cet élément est nécessaire; dans tous les autres cas, il est facultatif. Si cet élément est omis, `Group_Undefined:0` le parent de sera implicite.

## <a name="syntax"></a>Syntaxe

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID de l’identifiant de commande GUID/ID.|
|id|Obligatoire. ID de l’identifiant de commande GUID/ID.|

### <a name="child-elements"></a>Éléments enfants
 None

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes qu’un VSPackage fournit à l’environnement de développement intégré (IDE). Par exemple, les éléments de menu, les menus, les barres d’outils et les boîtes combo.|
|[Élément boutons](../extensibility/buttons-element.md)|Groupes [Éléments d’élément bouton.](../extensibility/button-element.md)|
|[Élément menus](../extensibility/menus-element.md)|Définit tous les menus qu’un VSPackage met en œuvre.|
|[Élément des groupes](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commande d’un VSPackage.|

## <a name="see-also"></a>Voir aussi
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
