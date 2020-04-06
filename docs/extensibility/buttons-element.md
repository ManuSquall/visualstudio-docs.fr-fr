---
title: Élément boutons Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64ac5621093f30af28ade0817906b767231e4ee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739917"
---
# <a name="buttons-element"></a>Élément boutons
Groupes [Éléments bouton,](../extensibility/button-element.md) qui représentent des commandes individuelles.

## <a name="syntax"></a>Syntaxe

```
<Buttons>
  <Button>... </Button>
  <Button>... </Button>
</Buttons>
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
|[Élément boutons](../extensibility/buttons-element.md)|Groupes Éléments bouton.|
|[Élément bouton](../extensibility/button-element.md)|Définit une commande avec laquelle l’utilisateur peut interagir.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de commande](../extensibility/commands-element.md)|Représente la collection de commandes sur la barre d’outils VSPackage.|

## <a name="example"></a>Exemple

```
<Buttons>
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>
    <Strings>
      <ButtonText>C# Command Sample</ButtonText>
    </Strings>
  </Button>
</Buttons>
```

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
