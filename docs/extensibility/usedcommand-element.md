---
title: Élément UsedCommand | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ea8f27cafb166968f66c53dc68398526e0aa5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718772"
---
# <a name="usedcommand-element"></a>Élément UsedCommand
Permet à un VSPackage d’accéder à une commande définie dans un autre fichier. vsct. Par exemple, si votre VSPackage utilise la commande de **copie** standard, qui est définie par le shell [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez ajouter la commande à un menu ou une barre d’outils sans la réimplémenter.

## <a name="syntax"></a>Syntaxe

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|uniques|Requis. GUID de la paire d’ID GUID qui identifie la commande.|
|ID|Requis. ID de la paire d’ID GUID qui identifie la commande.|
|Condition|Optionnel. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|aucune.||

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément UsedCommands](../extensibility/usedcommands-element.md)|Regroupe les éléments UsedCommand et d’autres regroupements UsedCommands.|

## <a name="remarks"></a>Notes
 En ajoutant une commande à l’élément `<UsedCommands>`, un VSPackage informe l’environnement [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que le VSPackage requiert la commande. Vous devez ajouter un élément `<UsedCommand>` pour toute commande dont votre package a besoin, qui n’est peut-être pas inclus dans toutes les versions et configurations de Visual Studio. Par exemple, si votre package appelle une commande qui est spécifique à Visual C++, la commande ne sera pas disponible pour les utilisateurs de Visual Web Developer, sauf si vous incluez un élément `<UsedCommand>` pour la commande.

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