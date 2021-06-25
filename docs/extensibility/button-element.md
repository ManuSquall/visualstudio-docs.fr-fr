---
title: Button, élément | Microsoft Docs
description: 'L’élément Button définit un élément avec lequel l’utilisateur peut interagir. Les boutons peuvent être des types différents : Button, MenuButton et SplitDropDown.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 630d848c40b13a929c3dd91b47e1c35529efaa50
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901745"
---
# <a name="button-element"></a>Button, élément
Définit un élément avec lequel l’utilisateur peut interagir. Les boutons peuvent être de différents types : Button, MenuButton et SplitDropDown.

## <a name="syntax"></a>Syntaxe

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID de l’identificateur de la commande GUID/ID.|
|id|Obligatoire. ID de l’identificateur de la commande GUID/ID.|
|priority|Optionnel. Valeur numérique qui spécifie la priorité.|
|type|Optionnel. Valeur énumérée qui spécifie le type de bouton.<br /><br /> S’il n’est pas spécifié, utilise le bouton.<br /><br /> Bouton<br /> Commande standard qui apparaît sur les barres d’outils (généralement sous la forme d’un bouton sous forme), menus et menus contextuels.<br /><br /> MenuButton<br /> Élément de menu qui n’exécute pas de commande, mais qui produit un autre menu.<br /><br /> SplitDropDown<br /> Contrôles, tels que les boutons Annuler et rétablir de la barre d’outils standard de Microsoft Word.|
|Condition|Optionnel. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément parent](../extensibility/parent-element.md)|Optionnel. Élément parent du bouton.|
|[Icon, élément](../extensibility/icon-element.md)|Optionnel. Icône associée au bouton.|
|[Élément d’indicateur de commande](../extensibility/command-flag-element.md)|Obligatoire. Les valeurs CommandFlag valides pour un bouton sont les suivantes.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> -Nocustom<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> -PICT<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> -Textchanges au<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> -TextOnly|
|[Élément Strings](../extensibility/strings-element.md)|Obligatoire. L' [élément ButtonText](../extensibility/buttontext-element.md) enfant doit être défini.|
|Annotation|Commentaire facultatif.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Buttons, élément](../extensibility/buttons-element.md)|Éléments du bouton groupes.|

## <a name="example"></a>Exemple
 L’exemple suivant définit un bouton dans un fichier *. vsct* .

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
