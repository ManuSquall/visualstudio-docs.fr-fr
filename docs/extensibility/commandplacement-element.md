---
title: Élément de commandement -md) Microsoft Docs
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
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739740"
---
# <a name="commandplacement-element"></a>Élément CommandPlacement
L’élément CommandPlacement permet d’inclure des boutons, des groupes et des menus dans plus d’un groupe ou un menu. En utilisant l’élément CommandPlacement, vous n’avez pas à redéfinir complètement ces éléments afin de modifier l’apparence d’une interface utilisateur.

 Pour plus d’informations, voir [Créer des groupes réutilisables de boutons](../extensibility/creating-reusable-groups-of-buttons.md).

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
|guid|Obligatoire. Le guid de l’ensemble de commande, tel que défini dans [l’élément Symboles](../extensibility/symbols-element.md).|
|id|Obligatoire. L’id du menu, du groupe ou de la `Symbols Element`commande à placer, tel que défini dans le .|
|priority|Obligatoire. Détermine la position visuelle de l’élément dans son élément parent.|
|Condition|facultatif. Voir [Aattributes conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Parent|Obligatoire. Le menu ou le groupe qui accueille l’article à placer.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandPlacements](../extensibility/commandplacements-element.md)|Spécifie des groupes de CommandPlacements et d’éléments commandPlacement.|

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
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
