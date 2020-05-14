---
title: Élément de commandement utilisé (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698823"
---
# <a name="usedcommand-element"></a>Élément UsedCommand
Permet à un VSPackage d’accéder à une commande définie dans un autre fichier .vsct. Par exemple, si votre VSPackage utilise la commande [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Copy** standard, qui est définie par la coque, vous pouvez ajouter la commande à un menu ou une barre d’outils sans la ré-implémenter.

## <a name="syntax"></a>Syntaxe

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. Le GUID de la paire GUID ID qui identifie la commande.|
|id|Obligatoire. L’ID de la paire GUID ID qui identifie la commande.|
|Condition|facultatif. Voir [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|None||

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément UsedCommands](../extensibility/usedcommands-element.md)|Groupes utilisésCommand éléments et autres groupes UsedCommands.|

## <a name="remarks"></a>Notes
 En ajoutant une `<UsedCommands>` commande à l’élément, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un VSPackage informe l’environnement que le VSPackage nécessite la commande. Vous devez `<UsedCommand>` ajouter un élément pour toute commande dont votre colis nécessite qui pourrait ne pas être inclus dans toutes les versions et configurations de Visual Studio. Par exemple, si votre forfait appelle une commande spécifique à Visual C, la commande ne sera `<UsedCommand>` pas disponible pour les utilisateurs de Visual Web Developer, sauf si vous incluez un élément pour la commande.

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
