---
title: Group, élément | Microsoft Docs
description: L’élément Group définit un groupe de commandes VSPackage. Cet article décrit les attributs, les éléments enfants et les éléments parents.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a5520a8a47b4b356a79832b619395f86e8231d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945784"
---
# <a name="group-element"></a>élément Group
Définit un groupe de commandes VSPackage.

## <a name="syntax"></a>Syntaxe

```xml
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">
  <Parent>... </Parent>
</Group>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID de l’identificateur de la commande GUID/ID.|
|id|Obligatoire. ID de l’identificateur de la commande GUID/ID.|
|priority|Facultatif. Valeur numérique qui spécifie la priorité.|
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Parent|Facultatif. Élément parent du bouton.|
|Annotation|Commentaire facultatif.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commandes d’un VSPackage.|

## <a name="example"></a>Exemple

```xml
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
</Group>
```

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
