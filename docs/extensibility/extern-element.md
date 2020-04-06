---
title: Élément externe (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711487"
---
# <a name="extern-element"></a>Élément extern
L’élément Extern fait référence à tous les fichiers d’en-tête externes (*.h)* à fusionner avec le fichier *.vsct* au moment de la compilation. Les fichiers à fusionner doivent être sur la voie d’inclure donnée au compilateur VSCT ou référencé par un [élément Inclure](../extensibility/include-element.md). Les fichiers peuvent être d’autres fichiers *.vsct* ou fichiers d’en-tête C.

 Définitions dans les fichiers d’en-tête doit être du formulaire "#define [Symbole] [Valeur]" La valeur peut être un autre symbole si elle est précédemment définie. Les définitions peuvent être utilisées dans les énoncés conditionnels des éléments de commandement. Tout symbole qui n’est pas réellement utilisé sera jeté.

 Élément externe d’élément de commande

## <a name="syntax"></a>Syntaxe

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|href|Obligatoire. Le chemin vers le fichier d’en-tête:<br /><br /> href "stdidcmd.h"|
|Condition|facultatif. Voir [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|langage|facultatif. Le langage par [ \<](../extensibility/strings-element.md) défaut de toutes les cordes>éléments dans le tableau de commande :<br /><br /> langue "en-nous"|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Aucun.|Aucun.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes — c’est-à-dire les éléments de menu, les menus, les barres d’outils et les boîtes combo — qu’un VSPackage fournit à l’IDE.|

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
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
