---
title: Élément Commandplacement ayant | Microsoft Docs
description: L’élément Commandplacement ayant permet d’inclure des boutons, des groupes et des menus dans plusieurs groupes ou menus.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2828a32ea837e95be438aafa6ec4b31293a43a7
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974059"
---
# <a name="commandplacement-element"></a>Élément Commandplacement ayant
L’élément Commandplacement ayant permet d’inclure des boutons, des groupes et des menus dans plusieurs groupes ou menus. À l’aide de l’élément Commandplacement ayant, il n’est pas nécessaire de redéfinir complètement ces éléments pour modifier l’apparence d’une interface utilisateur.

 Pour plus d’informations, consultez [créer des groupes de boutons réutilisables](../extensibility/creating-reusable-groups-of-buttons.md).

## <a name="syntax"></a>Syntaxe

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID du jeu de commandes, tel que défini dans l' [élément Symbols](../extensibility/symbols-element.md).|
|id|Obligatoire. ID du menu, du groupe ou de la commande à placer, tel que défini dans le `Symbols Element` .|
|priority|Obligatoire. Détermine la position visuelle de l’élément dans son élément parent.|
|Condition|facultatif. Consultez [Aattributes conditionnel](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Parent|Obligatoire. Le menu ou le groupe qui héberge l’élément à placer.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandPlacements](../extensibility/commandplacements-element.md)|Spécifie des groupes d’éléments CommandPlacements et Commandplacement ayant.|

## <a name="example"></a>Exemple

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Voir aussi
- [Élément CommandPlacements](../extensibility/commandplacements-element.md)
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
