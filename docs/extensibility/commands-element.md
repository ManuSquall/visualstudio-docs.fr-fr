---
title: Éléments de commande Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739683"
---
# <a name="commands-element"></a>Élément Commands
Représente la collection de commandes sur la barre d’outils VSPackage. La collection peut avoir jusqu’à cinq sous-sections, comme suit: menus, groupes, boutons, combos, et bitmaps.

 Chaque élément enfant de sous-section, par exemple, \<Menu>, est identifié par un ID de commande unique qui est une paire d’identification GUID et numérique. Le GUID identifie l'« ensemble de commande » et est utilisé pour regrouper les commandes logiquement liées. Le VSPackage devrait définir son propre ensemble de commandes pour éviter les collisions avec des Œd de commande qui sont définis par d’autres VSPackages.

## <a name="syntax"></a>Syntaxe

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|package|Un GUID qui identifie le VSPackage qui fournit les commandes.<br /><br /> Par exemple, forfait "guidVsPackage1Pkg".|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément menus](../extensibility/menus-element.md)|Définit tous les menus qu’un VSPackage met en œuvre.|
|[Élément des groupes](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commande dans un VSPackage.|
|[Élément boutons](../extensibility/buttons-element.md)|Groupes Éléments bouton.|
|[Élément Bitmaps](../extensibility/bitmaps-element.md)|Groupes Bitmap éléments.|
|[Élément Combos](../extensibility/combos-element.md)|Groupes Éléments Combo.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes qu’un VSPackage fournit à l’IDE. Les éléments possibles sont les éléments de menu, les menus, les barres d’outils et les boîtes combo.|

## <a name="example"></a>Exemple
 L’exemple suivant montre comment utiliser un [élément de commande](../extensibility/commands-element.md).

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
