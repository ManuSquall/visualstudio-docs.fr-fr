---
title: Élément VisibilityConstraints | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dfbeb3c45e05c93554aae9b17a42c265408bc3
ms.sourcegitcommit: f17e3afa5c324595afccf15a8a69df8c33b873d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658877"
---
# <a name="visibilityconstraints-element"></a>Élément VisibilityConstraints
L’élément VisibilityConstraints détermine la visibilité statique de groupes de commandes et des barres d’outils. La visibilité est tout d’abord contrôlée par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) sans charger le VSPackage.

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
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Détermine la visibilité statique de groupes de commandes et des barres d’outils.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes (par exemple, les éléments de menu, menus, barres d’outils et zones de liste déroulante) qu’un VSPackage fournit à l’IDE.|

## <a name="example"></a>Exemple

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Voir aussi
- [Élément VisibilityItem](../extensibility/visibilityitem-element.md)
- [Table de commande Visual Studio (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
