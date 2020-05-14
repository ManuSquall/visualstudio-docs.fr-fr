---
title: Élément VisibilitéItem Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698150"
---
# <a name="visibilityitem-element"></a>Élément VisibilitéItem
L’élément `VisibilityItem` détermine la visibilité statique des commandes et des barres d’outils. Chaque entrée identifie une commande ou un menu, ainsi qu’un contexte d’interface utilisateur de commande associé. Visual Studio détecte les commandes, les menus et les barres d’outils, et leur visibilité, sans charger les VSPackages qui les définissent. L’IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> utilise la méthode pour déterminer si un contexte d’interface utilisateur de commande est actif.

 Une fois le VSPackage chargé, Visual Studio s’attend à ce `VisibilityItem`que la visibilité de commande soit déterminée par le VSPackage plutôt que par le . Pour déterminer la visibilité de votre commande, vous pouvez implémenter le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestionnaire d’événements ou la méthode, selon la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> façon dont vous avez implémenté votre commande.

 Une commande ou un `VisibilityItem` menu qui a un élément n’apparaît que lorsque le contexte associé est actif. Vous pouvez associer une seule commande, menu ou barre d’outils à un ou plusieurs contextes d’interface utilisateur de commande en incluant une entrée pour chaque combinaison de contrôle-contexte. Si une commande ou un menu est associé à plusieurs contextes d’interface utilisateur de commande, la commande ou le menu est visible lorsque l’un des contextes d’interface utilisateur de commande associés est actif.

 L’élément `VisibilityItem` ne s’applique qu’aux commandes, aux menus et aux barres d’outils, et non aux groupes. Un élément qui n’a pas d’élément connexe `VisibilityItem` est visible chaque fois que son menu parent est actif.

## <a name="syntax"></a>Syntaxe

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. Le GUID de l’identifiant de commande GUID/ID.|
|id|Obligatoire. L’ID de l’identifiant de commande GUID/ID.|
|contexte|Obligatoire. Le contexte de l’interface utilisateur dans lequel la commande est visible.|
|Condition|facultatif. Voir [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants
 None

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[VisibilityConstraints élément](../extensibility/visibilityconstraints-element.md)|L’élément `VisibilityConstraints` détermine la visibilité statique des groupes de commandes et de barres d’outils.|

## <a name="remarks"></a>Notes
 Les contextes standard de l’interface utilisateur Visual Studio sont définis dans le *parcours d’installation Visual Studio SDK*'VisualStudioIntegration’Common’vsshlids.h fichier ainsi que dans le <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> fichier et <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> les classes. Un ensemble plus complet de contextes <xref:Microsoft.VisualStudio.VSConstants> d’interface utilisateur est défini dans la classe.

## <a name="example"></a>Exemple

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [VisibilityConstraints élément](../extensibility/visibilityconstraints-element.md)
- [Table de commande Visual Studio (. Vsct) Fichiers](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
