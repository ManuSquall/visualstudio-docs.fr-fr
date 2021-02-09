---
title: Élément VisibilityConstraints | Microsoft Docs
description: L’élément VisibilityConstraints détermine la visibilité statique des groupes de commandes et des barres d’outils.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb6047c98031c484f6a0a51ab2a393a2a46bb2a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926093"
---
# <a name="visibilityconstraints-element"></a>Élément VisibilityConstraints
L’élément VisibilityConstraints détermine la visibilité statique des groupes de commandes et des barres d’outils. La visibilité est tout d’abord contrôlée par l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE) sans charger le VSPackage.

## <a name="syntax"></a>Syntaxe

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément VisibilityItem](../extensibility/visibilityitem-element.md)|Détermine la visibilité statique des commandes et des barres d’outils.|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Détermine la visibilité statique des groupes de commandes et des barres d’outils.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes (par exemple, les éléments de menu, les menus, les barres d’outils et les zones de liste déroulante) qu’un VSPackage fournit à l’IDE.|

## <a name="example"></a>Exemple

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Voir aussi
- [Élément VisibilityItem](../extensibility/visibilityitem-element.md)
- [Table de commandes Visual Studio (. Fichiers vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
