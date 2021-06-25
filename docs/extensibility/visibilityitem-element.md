---
title: Élément VisibilityItem | Microsoft Docs
description: L’élément VisibilityItem détermine la visibilité statique des commandes et des barres d’outils. Les entrées identifient une commande ou un menu, ainsi qu’un contexte d’interface utilisateur de commande associé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 025e05dd0346c7da0a70985aa579d1673f2ffcaa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905434"
---
# <a name="visibilityitem-element"></a>Élément VisibilityItem
L' `VisibilityItem` élément détermine la visibilité statique des commandes et des barres d’outils. Chaque entrée identifie une commande ou un menu, ainsi qu’un contexte d’interface utilisateur de commande associé. Visual Studio détecte les commandes, les menus et les barres d’outils, ainsi que leur visibilité, sans charger les VSPackages qui les définissent. L’IDE utilise la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> méthode pour déterminer si un contexte d’interface utilisateur de commande est actif.

 Une fois le VSPackage chargé, Visual Studio attend que la visibilité de la commande soit déterminée par le VSPackage plutôt que par le `VisibilityItem` . Pour déterminer la visibilité de votre commande, vous pouvez implémenter le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Gestionnaire d’événements ou la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode, en fonction de la façon dont vous avez implémenté votre commande.

 Une commande ou un menu contenant un `VisibilityItem` élément apparaît uniquement lorsque le contexte associé est actif. Vous pouvez associer une commande, un menu ou une barre d’outils unique à un ou plusieurs contextes d’interface utilisateur de commande en incluant une entrée pour chaque combinaison de contexte de commande. Si une commande ou un menu est associé à plusieurs contextes d’interface utilisateur de commande, la commande ou le menu est visible quand l’un des contextes d’interface utilisateur de commande associés est actif.

 L' `VisibilityItem` élément s’applique uniquement aux commandes, menus et barres d’outils, pas aux groupes. Un élément qui n’a pas d' `VisibilityItem` élément associé est visible chaque fois que son menu parent est actif.

## <a name="syntax"></a>Syntaxe

```xml
<VisibilityItem
  guid="cmdGuidMyProductCommands"
  id="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID de l’identificateur de la commande GUID/ID.|
|id|Obligatoire. ID de l’identificateur de la commande GUID/ID.|
|contexte|Obligatoire. Contexte de l’interface utilisateur dans lequel la commande est visible.|
|Condition|Optionnel. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants
 Aucun

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|L' `VisibilityConstraints` élément détermine la visibilité statique des groupes de commandes et des barres d’outils.|

## <a name="remarks"></a>Remarques
 Les contextes d’interface utilisateur standard de Visual Studio sont définis dans le fichier \VisualStudioIntegration\Common\Inc\vsshlids.h du *chemin d’installation du kit de développement logiciel Visual Studio*, ainsi que dans les <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classes et. Un ensemble plus complet de contextes d’interface utilisateur est défini dans la <xref:Microsoft.VisualStudio.VSConstants> classe.

## <a name="example"></a>Exemple

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [Élément VisibilityConstraints](../extensibility/visibilityconstraints-element.md)
- [Table de commandes Visual Studio (. Fichiers vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
