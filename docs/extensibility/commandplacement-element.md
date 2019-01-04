---
title: Élément CommandPlacement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5d694f6ed12d3fd7d531ec6a0a01ec70a826561
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941353"
---
# <a name="commandplacement-element"></a>Élément CommandPlacement
L’élément CommandPlacement permet de boutons, des groupes et des menus être inclus dans plus d’un groupe ou un menu. À l’aide de l’élément CommandPlacement, il est inutile de redéfinir intégralement ces éléments afin de modifier l’apparence d’une interface utilisateur.  
  
 Pour plus d’informations, consultez [créer des groupes de boutons réutilisables](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire. Le guid du jeu de commandes, tel que défini dans le [élément Symbols](../extensibility/symbols-element.md).|  
|ID|Obligatoire. L’id du menu, un groupe ou une commande à placer, tel que défini dans le `Symbols Element`.|  
|priority|Obligatoire. Détermine la position visuelle de l’élément dans son élément parent.|  
|Condition|Facultatif. Consultez [Aattributes conditionnel](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent|Obligatoire. Le menu ou un groupe qui héberge l’élément à être placé.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandPlacements](../extensibility/commandplacements-element.md)|Spécifie les groupes d’éléments CommandPlacements et CommandPlacement.|  
  
## <a name="example"></a>Exemple  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CommandPlacements](../extensibility/commandplacements-element.md)   
 [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
