---
title: Élément parent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c025957bd0d3cf06bf73e1b35b5faa661386a0a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902435"
---
# <a name="parent-element"></a>Élément parent
Le parent d’un bouton ou une zone peut être uniquement un groupe. Le parent d’un menu ou un groupe peut être n’importe quel autre menu ou un groupe. Dans un [élément CommandPlacement](../extensibility/commandplacement-element.md), cet élément est requis ; il est facultatif dans toutes les autres instances. Si cet élément est omis, le parent de `Group_Undefined:0` est implicite.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire. Identificateur de commande de GUID/ID GUID.|  
|ID|Obligatoire. Identificateur de commande d’ID de/ID GUID.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes qu’un VSPackage fournit à l’environnement de développement intégré (IDE). Par exemple, les éléments de menu, menus, barres d’outils et zones de liste déroulante.|  
|[Élément Buttons](../extensibility/buttons-element.md)|Groupes [élément Button](../extensibility/button-element.md) éléments.|  
|[Élément menus](../extensibility/menus-element.md)|Définit tous les menus qui implémente un VSPackage.|  
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commandes d’un VSPackage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)