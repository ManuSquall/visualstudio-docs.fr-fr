---
title: "&#201;l&#233;ment de VisibilityConstraints | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisibilityConstraints"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, VisibilityConstraints"
  - "VisibilityConstraints, élément (schéma XML de VSCT)"
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# &#201;l&#233;ment de VisibilityConstraints
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément VisibilityConstraints détermine la visibilité statique de groupes de commandes et barres d'outils. La visibilité est tout d'abord contrôlée par la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'environnement de développement intégré \(IDE\) sans charger le VSPackage.  
  
## Syntaxe  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de VisibilityItem](../extensibility/visibilityitem-element.md)|Détermine la visibilité des commandes et des barres d'outils statique.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Détermine la visibilité des groupes de barres d'outils et commandes statique.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes \(par exemple, des éléments de menu, menus, barres d'outils et zones de liste déroulante\) un VSPackage fournit à l'IDE.|  
  
## Exemple  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## Voir aussi  
 [Élément de VisibilityItem](../extensibility/visibilityitem-element.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)