---
title: Élément parent | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2086473bc484fed4e8e351f0c3838074557586c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194075"
---
# <a name="parent-element"></a>Élément parent
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le parent d’un bouton ou d’une zone de liste déroulante ne peut être qu’un groupe. Le parent d’un menu ou d’un groupe peut être n’importe quel autre menu ou groupe. Dans un [élément commandplacement ayant](../extensibility/commandplacement-element.md), cet élément est obligatoire. dans toutes les autres instances, il est facultatif. Si cet élément est omis, le parent de `Group_Undefined:0` est implicite.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|guid|Obligatoire. GUID de l’identificateur de commande GUID/ID.|  
|id|Obligatoire. ID de l’identificateur de la commande GUID/ID.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes qu’un VSPackage fournit à l’environnement de développement intégré (IDE). Par exemple, les éléments de menu, les menus, les barres d’outils et les zones de liste modifiable.|  
|[Élément Buttons](../extensibility/buttons-element.md)|Éléments du [bouton](../extensibility/button-element.md) groupes.|  
|[Élément Menus](../extensibility/menus-element.md)|Définit tous les menus qu’un VSPackage implémente.|  
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commandes d’un VSPackage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
