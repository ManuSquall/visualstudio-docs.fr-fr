---
title: Commands, élément | Microsoft Docs
description: 'L’élément Commands représente la collection de commandes dans la barre d’outils VSPackage et peut contenir les sections suivantes : menus, groupes, boutons, combos et bitmaps.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4c7b058acdd634079d0ca60dddb9f80e0e26ff0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901868"
---
# <a name="commands-element"></a>Élément Commands
Représente la collection de commandes dans la barre d’outils VSPackage. La collection peut contenir jusqu’à cinq sous-sections, comme suit : menus, groupes, boutons, combos et bitmaps.

 Chaque élément enfant de sous-section, par exemple, \<Menu> est identifié par un ID de commande unique qui est un GUID et une paire d’identificateurs numériques. Le GUID identifie le « jeu de commandes » et est utilisé pour regrouper les commandes associées de manière logique. Le VSPackage doit définir son propre jeu de commandes pour éviter les collisions avec les ID de commande définis par d’autres VSPackages.

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
|package|GUID qui identifie le VSPackage qui fournit les commandes.<br /><br /> Par exemple, package = "guidVsPackage1Pkg".|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément menus](../extensibility/menus-element.md)|Définit tous les menus qu’un VSPackage implémente.|
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commandes dans un VSPackage.|
|[Buttons, élément](../extensibility/buttons-element.md)|Éléments du bouton groupes.|
|[Élément bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments bitmap.|
|[Élément combos](../extensibility/combos-element.md)|Regroupe les éléments de liste.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes qu’un VSPackage fournit à l’IDE. Les éléments possibles sont les éléments de menu, les menus, les barres d’outils et les zones de liste modifiable.|

## <a name="example"></a>Exemple
 L’exemple suivant montre comment utiliser un [élément Commands](../extensibility/commands-element.md).

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
- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
