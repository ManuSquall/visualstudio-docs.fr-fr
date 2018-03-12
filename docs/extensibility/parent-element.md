---
title: "Élément parent | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4f2209ce2a2f6b1263bb52d550ca303f2525047d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="parent-element"></a>Parent, élément
Le parent d’un bouton ou une zone peut être uniquement un groupe. Le parent d’un menu ou un groupe peut être n’importe quel autre menu ou un groupe. Dans un [CommandPlacement élément](../extensibility/commandplacement-element.md), cet élément est requis ; dans tous les autres cas, il est facultatif. Si cet élément est omis, le parent de `Group_Undefined:0` sera être déduit.  
  
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
|ID|Obligatoire. Identificateur de commande ID GUID/ID.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes par un VSPackage à l’environnement de développement intégré (IDE). Par exemple, des éléments de menu, menus, barres d’outils et zones de liste déroulante.|  
|[Élément Buttons](../extensibility/buttons-element.md)|Groupes [élément Button](../extensibility/button-element.md) éléments.|  
|[Élément Menus](../extensibility/menus-element.md)|Définit tous les menus un VSPackage implémente.|  
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commandes d’un VSPackage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)