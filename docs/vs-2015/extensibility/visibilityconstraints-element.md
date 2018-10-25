---
title: Élément VisibilityConstraints | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07b0638ae668f7daa39321f92ad92d8eb68a1ba3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881853"
---
# <a name="visibilityconstraints-element"></a>Élément VisibilityConstraints
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’élément VisibilityConstraints détermine la visibilité statique de groupes de commandes et des barres d’outils. La visibilité est tout d’abord contrôlée par le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE) sans charger le VSPackage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément VisibilityItem](../extensibility/visibilityitem-element.md)|Détermine la visibilité statique des commandes et des barres d’outils.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Détermine la visibilité statique de groupes de commandes et des barres d’outils.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes (par exemple, les éléments de menu, menus, barres d’outils et zones de liste déroulante) qu’un VSPackage fournit à l’IDE.|  
  
## <a name="example"></a>Exemple  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément VisibilityItem](../extensibility/visibilityitem-element.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

