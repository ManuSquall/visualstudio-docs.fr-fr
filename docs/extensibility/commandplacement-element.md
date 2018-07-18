---
title: Élément de CommandPlacement | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 49de1e1cb41c13ef9b587689f36e302bcadf890c
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267973"
---
# <a name="commandplacement-element"></a>Élément de CommandPlacement
L’élément CommandPlacement permet de boutons, des groupes et des menus être inclus dans plus d’un groupe ou un menu. À l’aide de l’élément CommandPlacement, vous n’avez pas complètement redéfinir ces éléments afin de modifier l’apparence d’une interface utilisateur.  
  
 Pour plus d’informations, consultez [création de groupes réutilisable de boutons](../extensibility/creating-reusable-groups-of-buttons.md).  
  
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
|GUID|Obligatoire. Le guid du jeu de commandes, tel que défini dans le [symboles élément](../extensibility/symbols-element.md).|  
|ID|Obligatoire. L’id du menu, groupe ou commande doit être placé, tel que défini dans le `Symbols Element`.|  
|priority|Obligatoire. Détermine la position visuelle de l’élément dans son élément parent.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent|Obligatoire. Le menu ou un groupe qui héberge l’élément doit être placé.|  
  
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
 [Élément de CommandPlacements](../extensibility/commandplacements-element.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
