---
title: Définir l’élément | Microsoft Docs
description: L’élément define définit un nom de symbole et une paire de valeurs. Ce symbole peut être évalué par des attributs conditionnels.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2a2686abd8e8c703d8fb85009b3ba56070f166f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968448"
---
# <a name="define-element"></a>Définir l’élément
Définit un nom de symbole et une paire de valeurs. Ce symbole peut être évalué par des attributs conditionnels. Pour plus d’informations, consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md). Voir aussi l' [élément Symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Syntaxe

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|name|Obligatoire. Nom du symbole :<br /><br /> Name = "mode"|
|valeur|Obligatoire. Valeur du symbole :<br /><br /> valeur = « standard »|
|Condition|Facultatif. Pour plus d’informations, consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes qu’un VSPackage fournit à l’environnement de développement intégré (IDE). Par exemple, les éléments de menu, les menus, les barres d’outils et les zones de liste modifiable.|

## <a name="example"></a>Exemple

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
