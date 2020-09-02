---
title: Élément UsedCommand | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698823"
---
# <a name="usedcommand-element"></a>Élément UsedCommand
Permet à un VSPackage d’accéder à une commande définie dans un autre fichier. vsct. Par exemple, si votre VSPackage utilise la commande de **copie** standard, qui est définie par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell, vous pouvez ajouter la commande à un menu ou une barre d’outils sans la réimplémenter.

## <a name="syntax"></a>Syntaxe

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID de la paire d’ID GUID qui identifie la commande.|
|id|Obligatoire. ID de la paire d’ID GUID qui identifie la commande.|
|Condition|facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|None||

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément UsedCommands](../extensibility/usedcommands-element.md)|Regroupe les éléments UsedCommand et d’autres regroupements UsedCommands.|

## <a name="remarks"></a>Notes
 En ajoutant une commande à l' `<UsedCommands>` élément, un VSPackage informe l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement que le VSPackage requiert la commande. Vous devez ajouter un `<UsedCommand>` élément pour toute commande dont votre package a besoin, qui peut ne pas être inclus dans toutes les versions et configurations de Visual Studio. Par exemple, si votre package appelle une commande qui est spécifique à Visual C++, la commande ne sera pas disponible pour les utilisateurs de Visual Web Developer, sauf si vous incluez un `<UsedCommand>` élément pour la commande.

## <a name="example"></a>Exemple

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Voir aussi
- [Élément UsedCommands](../extensibility/usedcommands-element.md)
- [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
