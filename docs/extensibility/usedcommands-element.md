---
title: Élément UsedCommands | Microsoft Docs
description: L’élément UsedCommands groupe les éléments UsedCommand et d’autres regroupements UsedCommands. L’élément UsedCommands est facultatif.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21233527c9fcfb97fd45a8eeed60c04927df8ba1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903032"
---
# <a name="usedcommands-element"></a>Élément UsedCommands
L’élément UsedCommands groupe les éléments UsedCommand et d’autres regroupements UsedCommands.

 L’élément UsedCommands est facultatif. Si vous n’appelez pas de commandes définies en dehors de votre package, vous n’avez pas besoin d’inclure cette section dans votre fichier. vsct.

## <a name="syntax"></a>Syntaxe

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
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
|[Élément UsedCommand](../extensibility/usedcommand-element.md)|Commande implémentée par un autre code.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes (par exemple, des éléments de menu, des menus, des barres d’outils et des zones de liste déroulante) qu’un VSPackage fournit à l’environnement de développement intégré (IDE).|

## <a name="example"></a>Exemple

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Voir aussi
- [Élément UsedCommand](../extensibility/usedcommand-element.md)
- [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
