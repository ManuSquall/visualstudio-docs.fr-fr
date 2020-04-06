---
title: VisibilityConstraints Élément Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1aaa9573b883910ac6fa5d921a9bc79ce1c1cf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698190"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints élément
L’élément VisibilityConstraints détermine la visibilité statique des groupes de commandes et des barres d’outils. La visibilité est d’abord contrôlée par l’environnement [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de développement intégré (IDE) sans charger le VSPackage.

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
|Condition|facultatif. Voir [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément VisibilitéItem](../extensibility/visibilityitem-element.md)|Détermine la visibilité statique des commandes et des barres d’outils.|
|[VisibilitéConstraints](../extensibility/visibilityconstraints-element.md)|Détermine la visibilité statique des groupes de commandes et de barres d’outils.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes (par exemple, les éléments de menu, les menus, les barres d’outils et les boîtes combo) qu’un VSPackage fournit à l’IDE.|

## <a name="example"></a>Exemple

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Voir aussi
- [Élément VisibilitéItem](../extensibility/visibilityitem-element.md)
- [Table de commande Visual Studio (. Vsct) fichiers](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
