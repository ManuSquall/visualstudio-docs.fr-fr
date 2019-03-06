---
title: Commandes d’élément | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 823a91f15ef1dca47e8fd58db0646cd5248cfb1f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684024"
---
# <a name="commands-element"></a>Élément Commands
Représente la collection de commandes sur la barre d’outils de VSPackage. La collection peut avoir jusqu'à cinq sous-sections, comme suit : menus, des groupes, des boutons, des combos et des bitmaps.

 Chaque élément enfant sous-section, par exemple, \<Menu >, est identifié par un ID de commande unique qui est un GUID et une paire d’identificateur numérique. Le GUID identifie le jeu de commandes « » et est utilisé pour regrouper les commandes liés logiquement entre eux. Le VSPackage doit définir son propre jeu de commandes pour éviter les collisions avec les ID de commande qui sont définies par les autres VSPackages.

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
|package|Un GUID qui identifie le VSPackage qui fournit les commandes.<br /><br /> Par exemple, un package = « guidVsPackage1Pkg ».|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément menus](../extensibility/menus-element.md)|Définit tous les menus qui implémente un VSPackage.|
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commandes dans un VSPackage.|
|[Élément Buttons](../extensibility/buttons-element.md)|Regroupe les éléments de bouton.|
|[Élément bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments de la Bitmap.|
|[Élément combos](../extensibility/combos-element.md)|Regroupe les éléments de liste déroulante.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes qu’un VSPackage fournit à l’IDE. Éléments possibles sont les éléments de menu, des menus, des barres d’outils et des zones de liste déroulante.|

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
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)