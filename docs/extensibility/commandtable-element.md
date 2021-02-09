---
title: Élément CommandTable | Microsoft Docs
description: CommandTable est l’élément racine du fichier. vsct, qui définit la disposition et le type des commandes qu’un VSPackage fournit à l’IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79441880091088cf1d953c8925273e801dc0860d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887352"
---
# <a name="commandtable-element"></a>Élément CommandTable
CommandTable est l’élément racine du fichier *. vsct* . Il s’agit du fichier qui définit la disposition et le type réels des commandes qu’un VSPackage fournit à l’IDE. Les commandes peuvent inclure des éléments de menu, des menus, des barres d’outils et des zones de liste modifiable. Pour plus d’informations, consultez [fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="syntax"></a>Syntaxe

```xml
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >
  <Extern>... </Extern>
  <Include>... </Include>
  <Define>... </Define>
  <Commands>... </Commands>
  <CommandPlacements>... </CommandPlacements>
  <VisibilityConstraints>... </VisibilityConstraints>
  <KeyBindings>... </KeyBindings>
  <UsedCommands... </UsedCommands>
  <Symbols>... </Symbols>
</CommandTable>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

| Attribut | Description |
|-----------| - |
| xmlns | Obligatoire. Espaces de noms XML :<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns : XS = " <http://www.w3.org/2001/XMLSchema> " |
| langage | Facultatif. L’attribut Language peut être utilisé pour spécifier la langue par défaut de tous les \<Strings> éléments de la table Command.  Si la langue n’est pas spécifiée, la langue du processus en cours sera utilisée :<br /><br /> Language = "en-US" |

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément extern](../extensibility/extern-element.md)|Facultatif. Contient des directives de préprocesseur pour le compilateur.|
|[Élément Include](../extensibility/include-element.md)|Facultatif. Contient les chemins d’accès à tous les fichiers à inclure dans la compilation.|
|[Définir l’élément](../extensibility/define-element.md)|Facultatif. Définit un symbole en fonction de son nom et de sa valeur.|
|[Élément Commands](../extensibility/commands-element.md)|Facultatif. Élément parent qui définit toutes les commandes pour le VSPackage qui contient tous les autres éléments.|
|[Élément CommandPlacements](../extensibility/commandplacements-element.md)|Facultatif. Définit l’emplacement où les commandes doivent être placées dans la barre de commandes.|
|[Élément VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Facultatif. Détermine la visibilité statique des commandes et des barres d’outils.|
|[KeyBindings (élément)](../extensibility/keybindings-element.md)|Facultatif. Spécifie les combinaisons de touches de raccourci, le cas échéant, pour les commandes.|
|[Élément UsedCommands](../extensibility/usedcommands-element.md)|Facultatif. Permet à un VSPackage d’implémenter éventuellement sa propre version de fonctionnalité prise en charge à l’origine par d’autres VSPackages.|
|[Élément Symbols](https://www.microsoft.com/download/details.aspx?id=55984)|Facultatif. Contient des données de symboles (GUID, ID, etc.) pour le compilateur.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|None||

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
