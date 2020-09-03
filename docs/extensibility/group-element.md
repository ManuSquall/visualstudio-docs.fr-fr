---
title: Group, élément | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26479257511d74f122dd4064330f5b6a1e8dadd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711232"
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
|priority|facultatif. Valeur numérique qui spécifie la priorité.|
|Condition|facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Parent|facultatif. Élément parent du bouton.|
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
