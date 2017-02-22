---
title: "&#201;l&#233;ment de VisibilityItem | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VisibilityItem, élément (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, VisibilityItem"
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# &#201;l&#233;ment de VisibilityItem
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le `VisibilityItem` détermine la visibilité des commandes et des barres d'outils statique. Chaque entrée identifie une commande ou un menu et également un contexte de l'interface utilisateur de commande associée. Visual Studio détecte les commandes, menus et barres d'outils et leur visibilité, sans charger les VSPackages qui les définissent. L'IDE utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> méthode pour déterminer si un contexte de l'interface utilisateur de commande est actif.  
  
 Après le chargement du package VS, Visual Studio attend la visibilité de commande doit être déterminé par le VSPackage plutôt que `VisibilityItem`. Pour déterminer la visibilité de votre commande, vous pouvez implémenter la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Gestionnaire d'événements ou la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \(méthode\), selon la façon dont vous avez implémenté votre commande.  
  
 Une commande ou un menu qui a un `VisibilityItem` élément apparaît uniquement lorsque le contexte associé est actif. Vous pouvez associer une commande unique, un menu ou une barre d'outils avec un ou plusieurs contextes d'interface utilisateur de commande en incluant une entrée pour chaque combinaison de contexte de la commande. Si une commande ou un menu est associé à plusieurs contextes d'interface utilisateur de commande, puis la commande ou le menu est visible lorsque l'un des contextes d'interface utilisateur de la commande associée est actif.  
  
 Le `VisibilityItem` élément s'applique uniquement aux commandes, menus et barres d'outils, pas aux groupes. Un élément qui n'a pas une `VisibilityItem` élément est visible lorsque son menu parent est actif.  
  
## Syntaxe  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|GUID|Obligatoire. Le GUID de l'identificateur de commande\/ID GUID.|  
|ID|Obligatoire. ID de l'identificateur de commande\/ID GUID.|  
|contexte|Obligatoire. Le contexte de l'interface utilisateur dans lequel la commande est visible.|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Le `VisibilityConstraints` détermine la visibilité des groupes de barres d'outils et commandes statique.|  
  
## Notes  
 Les contextes d'interface utilisateur de Visual Studio standards sont définis dans le *chemin d'installation de Visual Studio SDK*\\VisualStudioIntegration\\Common\\Inc\\vsshlids.h le fichier ainsi que dans les <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> et <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classes. Un ensemble plus complet des contextes d'interface utilisateur est défini dans la <xref:Microsoft.VisualStudio.VSConstants> classe.  
  
## Exemple  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Élément de VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)