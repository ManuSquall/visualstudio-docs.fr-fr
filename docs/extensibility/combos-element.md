---
title: Élément Combos (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d005ea69aea7f0331877326abe4087fcff403553
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739803"
---
# <a name="combos-element"></a>Élément Combos
Éléments [d’élément Combo](../extensibility/combo-element.md) de groupes.

## <a name="syntax"></a>Syntaxe

```
<Combos>
  <Combo>... </Combo>
  <Combo>... </Combo>
</Combos>
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
|[Élément Combos](../extensibility/combos-element.md)|Groupes Éléments Combo.|
|[Élément Combo](../extensibility/combo-element.md)|Définit les commandes qui apparaissent dans une boîte combo.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de commande](../extensibility/commands-element.md)|Représente la collection de commandes sur la barre d’outils VSPackage.|

## <a name="example"></a>Exemple

```
<Combos>
  <Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
    defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
    <CommandFlag>DynamicVisibility</CommandFlag>
    <Strings>
      <ButtonText>Select Insert Options</ButtonText>
    </Strings>
  </Combo>

  <Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0500" type="DropDownCombo" defaultWidth="100"
    idCommandList="cmdidGetInsertOptionsList">
    <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <CommandFlag>DynamicVisibility</CommandFlag>
    <Strings>
      <ButtonText>Select Insert Options</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
