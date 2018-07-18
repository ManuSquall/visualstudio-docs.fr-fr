---
title: Élément de VisibilityItem | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85cc2a3d65d5a4763aeca231175201cf55a74b3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143463"
---
# <a name="visibilityitem-element"></a>Élément de VisibilityItem
Le `VisibilityItem` élément détermine la visibilité statique des commandes et des barres d’outils. Chaque entrée identifie une commande ou un menu et également un contexte de l’interface utilisateur de commande associée. Visual Studio détecte les commandes, menus et barres d’outils et leur visibilité, sans charger les VSPackages qui les définissent. L’IDE utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> méthode pour déterminer si un contexte de l’interface utilisateur de commande est actif.  
  
 Une fois le VSPackage est chargé, Visual Studio attend la visibilité de commande est déterminée par le VSPackage plutôt que `VisibilityItem`. Pour déterminer la visibilité de votre commande, vous pouvez implémenter soit le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Gestionnaire d’événements ou la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (méthode), selon la façon dont vous avez implémenté votre commande.  
  
 Une commande ou un menu qui a un `VisibilityItem` élément apparaît uniquement lorsque le contexte associé est actif. Vous pouvez associer une commande unique, un menu ou une barre d’outils avec un ou plusieurs contextes d’interface utilisateur de commande en incluant une entrée pour chaque combinaison de contexte de la commande. Si une commande ou un menu est associé à plusieurs contextes d’interface utilisateur de commande, puis la commande ou un menu est visible lorsque l’un des contextes d’interface utilisateur de la commande associée est actif.  
  
 Le `VisibilityItem` élément s’applique uniquement aux commandes, menus et barres d’outils, pas aux groupes. Un élément qui n’a pas un `VisibilityItem` élément est visible lorsque son menu parent est actif.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|GUID|Obligatoire. Le GUID de l’identificateur de commande/ID GUID.|  
|ID|Obligatoire. ID de l’identificateur de commande/ID GUID.|  
|contexte|Obligatoire. Le contexte de l’interface utilisateur dans laquelle la commande est visible.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Le `VisibilityConstraints` élément détermine la visibilité statique de groupes de commandes et des barres d’outils.|  
  
## <a name="remarks"></a>Notes  
 Les contextes d’interface utilisateur Visual Studio standards sont définis dans le *chemin d’installation de Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h fichier ainsi que dans les <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> et <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classes. Un ensemble plus complet de contextes d’interface utilisateur est défini dans la <xref:Microsoft.VisualStudio.VSConstants> classe.  
  
## <a name="example"></a>Exemple  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Élément de VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)