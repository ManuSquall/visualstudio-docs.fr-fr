---
title: Élément KeyBinding (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703144"
---
# <a name="keybinding-element"></a>Élément KeyBinding
L’élément KeyBinding spécifie les raccourcis clavier pour les commandes.

 Les commandes peuvent avoir des liaisons à clé unique et double qui leur sont associées. Un exemple d’une liaison clé unique est **Ctrl**+**S** pour la commande **Save.** Les liaisons à deux clés nécessitent deux combinaisons de clés successives pour déclencher une commande. Un exemple d’une liaison à double clé est <strong>Ctrl*+</strong>K<strong>,</strong><strong>+</strong>Ctrl K*- pour définir un signet.

## <a name="syntax"></a>Syntaxe

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire.|
|id|Obligatoire.|
|éditeur|Obligatoire. L’éditeur GUID indique le contexte d’édition pour lequel ce raccourci clavier sera actif. La valeur globale de portée contraignante est "guidVSStd97".|
|key1|Obligatoire. Les valeurs valides incluent tous les alphanumériques typables, et aussi les valeurs hexadecimal à deux chiffres précédées par 0x et [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|facultatif. Toute combinaison de **Ctrl**, **Alt**, et **Shift** séparés par l’espace.|
|key2|facultatif. Les valeurs valides incluent tous les alphanumériques typables, et aussi les valeurs hexadecimal à deux chiffres précédées par 0x et [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|facultatif. Toute combinaison de **Ctrl**, **Alt**, et **Shift** séparés par l’espace.|
|émulateur|facultatif.|
|Condition|facultatif. Voir [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Parent||
|Annotation||

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément KeyBindings](../extensibility/keybindings-element.md)|Groupes Éléments KeyBinding et autres groupes KeyBindings.|

## <a name="example"></a>Exemple

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>Voir aussi
- [Élément KeyBindings](../extensibility/keybindings-element.md)
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
