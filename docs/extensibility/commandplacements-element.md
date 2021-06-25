---
title: Élément CommandPlacements | Microsoft Docs
description: L’élément CommandPlacements groupe les éléments Commandplacement ayant et d’autres regroupements CommandPlacements. L’élément CommandPlacements est facultatif.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21e0feb3913b148b4320e69461bc5035655a392d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901888"
---
# <a name="commandplacements-element"></a>Élément CommandPlacements
L’élément CommandPlacements groupe les éléments Commandplacement ayant et d’autres regroupements CommandPlacements.

 L’élément CommandPlacements est facultatif. Si aucune commande, aucun groupe ou aucun menu ne doit être inclus dans un emplacement secondaire, vous n’avez pas besoin d’inclure cette section dans votre fichier *. vsct* .

## <a name="syntax"></a>Syntaxe

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|Condition|Optionnel. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|CommandPlacements|Regroupe les éléments Commandplacement ayant et d’autres regroupements CommandPlacements.|
|[Élément Commandplacement ayant](../extensibility/commandplacement-element.md)|Permet l’inclusion de boutons, de groupes et de menus dans plusieurs groupes ou menus.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes.|

## <a name="example"></a>Exemple

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Voir aussi
- [Élément Commandplacement ayant](../extensibility/commandplacement-element.md)
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
