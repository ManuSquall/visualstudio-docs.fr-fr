---
title: Élément bouton Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739929"
---
# <a name="button-element"></a>Élément bouton
Définit un élément avec lequel l’utilisateur peut interagir. Les boutons peuvent être de différentes sortes: Button, MenuButton, et SplitDropDown.

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
|guid|Obligatoire. GUID de l’identifiant de commande GUID/ID.|
|id|Obligatoire. ID de l’identifiant de commande GUID/ID.|
|priority|facultatif. Une valeur numérique qui spécifie la priorité.|
|type|facultatif. Une valeur énumérée qui spécifie le type de bouton.<br /><br /> Si elle n’est pas donnée, utilise Button.<br /><br /> Bouton<br /> Une commande standard qui apparaît sur les barres d’outils (généralement comme un bouton emblématique), des menus et des menus contextuels.<br /><br /> MenuButton<br /> Un élément de menu qui n’exécute pas une commande, mais produit un autre menu.<br /><br /> SplitDropDown (SplitDropDown)<br /> Contrôles, tels que les boutons Annuler et refaire sur la barre d’outils standard de Microsoft Word.|
|Condition|facultatif. Voir [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément parent](../extensibility/parent-element.md)|facultatif. L’élément parent du bouton.|
|[Élément d’icône](../extensibility/icon-element.md)|facultatif. L’icône associée au bouton.|
|[Élément de drapeau de commande](../extensibility/command-flag-element.md)|Obligatoire. Les valeurs commandflag valides pour un bouton sont les suivantes.<br /><br /> - Autoriser lesparams<br /><br /> - CommandWellOnly<br /><br /> - DéfautDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibilité<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> - Pict<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextChanges<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - TextOnly|
|[Élément cordes](../extensibility/strings-element.md)|Obligatoire. [L’élément ButtonText de l’enfant](../extensibility/buttontext-element.md) doit être défini.|
|Annotation|Commentaire facultatif.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément boutons](../extensibility/buttons-element.md)|Groupes Éléments bouton.|

## <a name="example"></a>Exemple
 L’exemple suivant définit un bouton dans un fichier *.vsct.*

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
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
