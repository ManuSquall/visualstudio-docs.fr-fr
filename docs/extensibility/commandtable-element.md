---
title: Élément De poste de commande (fr) Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739648"
---
# <a name="commandtable-element"></a>Élément CommandTable
CommandTable est l’élément racine du fichier *.vsct.* Il s’agit du fichier qui définit la mise en page réelle et le type des commandes qu’un VSPackage fournit à l’IDE. Les commandes peuvent inclure des éléments de menu, des menus, des barres d’outils et des boîtes combo. Pour plus d’informations, consultez [les fichiers visual Studio table de commande (.vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

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
| xmlns | Obligatoire. Espaces de noms XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs "<http://www.w3.org/2001/XMLSchema>" |
| langage | facultatif. L’attribut de langue peut être utilisé \<pour spécifier le langage par défaut de toutes les cordes> éléments dans le tableau de commande.  Si la langue n’est pas spécifiée, la langue du processus actuel sera utilisée :<br /><br /> langue "en-nous" |

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Élément extern](../extensibility/extern-element.md)|facultatif. Contient des directives préprocessoires pour le compilateur.|
|[Inclure l’élément](../extensibility/include-element.md)|facultatif. Contient des chemins vers tous les fichiers à inclure dans la compilateur.|
|[Définir l’élément](../extensibility/define-element.md)|facultatif. Définit un symbole donné son nom et sa valeur.|
|[Élément de commande](../extensibility/commands-element.md)|facultatif. L’élément parent définissant toutes les commandes pour le VSPackage qui contient tous les autres éléments.|
|[Élément CommandPlacements](../extensibility/commandplacements-element.md)|facultatif. Définit où sur la barre de commande les commandes doivent être placées.|
|[VisibilityConstraints élément](../extensibility/visibilityconstraints-element.md)|facultatif. Détermine la visibilité statique des commandes et des barres d’outils.|
|[Élément KeyBindings](../extensibility/keybindings-element.md)|facultatif. Spécifie les combinaisons de clés de raccourci, le cas échéant, pour les commandes.|
|[Élément Decommands usagé](../extensibility/usedcommands-element.md)|facultatif. Permet à un VSPackage d’implémenter optionnellement sa propre version de fonctionnalité à l’origine prise en charge par d’autres VSPackages.|
|[Élément symbole](https://www.microsoft.com/download/details.aspx?id=55984)|facultatif. Contient toutes les données du symbole -- GUIDs, IDs, etc. -- pour le compilateur.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|None||

## <a name="see-also"></a>Voir aussi
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
