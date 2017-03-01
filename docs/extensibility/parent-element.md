---
title: "Élément parent | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0da0bd0aceaccdbf8d2cf11fd3490a3e5810ad2e
ms.lasthandoff: 02/22/2017

---
# <a name="parent-element"></a>Parent, élément
Le parent d’un bouton ou une zone peut être uniquement un groupe. Le parent d’un menu ou d’un groupe peut être n’importe quel autre menu ou un groupe. Dans un [CommandPlacement élément](../extensibility/commandplacement-element.md), cet élément est obligatoire ; dans tous les autres cas, il est facultatif. Si cet élément est omis, le parent de `Group_Undefined:0` est impliquée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire. Identificateur de commande de GUID/ID GUID.|  
|ID|Obligatoire. ID de GUID/identificateur ID de commande.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes qui fournit un VSPackage à l’environnement de développement intégré (IDE). Par exemple, des éléments de menu, menus, barres d’outils et zones de liste déroulante.|  
|[Élément de boutons](../extensibility/buttons-element.md)|Groupes [élément Button](../extensibility/button-element.md) éléments.|  
|[Élément de menus](../extensibility/menus-element.md)|Définit tous les menus qui implémente un VSPackage.|  
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commande d’un VSPackage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Table de commandes de Visual Studio (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
