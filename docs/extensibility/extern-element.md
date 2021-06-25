---
title: Élément extern | Microsoft Docs
description: L’élément extern fait référence à tous les fichiers d’en-tête externes (. h) à fusionner avec le fichier. vsct au moment de la compilation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 502b93f18aacfed26d3ea440c017e6de5281a35d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900185"
---
# <a name="extern-element"></a>Élément extern
L’élément extern fait référence à tous les fichiers d’en-tête externes (*. h*) à fusionner avec le fichier *. vsct* au moment de la compilation. Les fichiers à fusionner doivent se trouver sur le chemin d’accès include donné au compilateur VSCT ou référencés par un [élément Include](../extensibility/include-element.md). Les fichiers peuvent être d’autres fichiers *. vsct* ou des fichiers d’en-tête C++.

 Les définitions des fichiers d’en-tête doivent être au format « #define [Symbol] [value] ». la valeur peut être un autre symbole s’il est défini précédemment. Les définitions peuvent être utilisées dans des instructions conditionnelles d’éléments de commande. Tout symbole qui n’est pas réellement utilisé sera ignoré.

 Élément CommandTable extern

## <a name="syntax"></a>Syntaxe

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|href|Obligatoire. Chemin d’accès au fichier d’en-tête :<br /><br /> href = "stdidcmd. h"|
|Condition|Optionnel. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|langage|Optionnel. Langue par défaut de tous les [\<Strings>](../extensibility/strings-element.md) éléments de la table de commandes :<br /><br /> Language = "en-US"|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Aucun.|Aucun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes, c’est-à-dire des éléments de menu, des menus, des barres d’outils et des zones de liste déroulante, qu’un VSPackage fournit à l’IDE.|

## <a name="example"></a>Exemple

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
