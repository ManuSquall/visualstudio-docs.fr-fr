---
title: KeyBinding, élément | Microsoft Docs
description: L’élément KeyBinding spécifie les raccourcis clavier pour les commandes. Les commandes peuvent être associées à des liaisons à clé unique et à deux clés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ce96da36a8c6eff0fda71d8a5d077721876ab8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943346"
---
# <a name="keybinding-element"></a>KeyBinding (élément)
L’élément KeyBinding spécifie les raccourcis clavier pour les commandes.

 Les commandes peuvent être associées à des liaisons à clé unique et à deux clés. Un exemple de liaison de clé unique est **CTRL** + **S** pour la commande **Enregistrer** . Les combinaisons de touches doubles requièrent deux combinaisons de touches successives pour déclencher une commande. Un exemple de liaison à double clé est <strong>CTRL *+</strong> k <strong>,</strong>Ctrl <strong>+</strong> k** pour définir un signet.

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
|éditeur|Obligatoire. Le GUID de l’éditeur indique le contexte d’édition pour lequel ce raccourci clavier est actif. La valeur de portée de liaison globale est « guidVSStd97 ».|
|key1|Obligatoire. Les valeurs valides incluent tous les alphanumériques typable, ainsi que les valeurs hexadécimales à deux chiffres précédées de 0x et [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|Facultatif. Toutes les combinaisons de **touches Ctrl**, **ALT** et **MAJ** sont séparées par un espace.|
|key2|Facultatif. Les valeurs valides incluent tous les alphanumériques typable, ainsi que les valeurs hexadécimales à deux chiffres précédées de 0x et [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Facultatif. Toutes les combinaisons de **touches Ctrl**, **ALT** et **MAJ** sont séparées par un espace.|
|émulateur|Facultatif.|
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Parent||
|Annotation||

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[KeyBindings (élément)](../extensibility/keybindings-element.md)|Groupe les éléments KeyBinding et d’autres regroupements de combinaisons de touches.|

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
- [KeyBindings (élément)](../extensibility/keybindings-element.md)
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
