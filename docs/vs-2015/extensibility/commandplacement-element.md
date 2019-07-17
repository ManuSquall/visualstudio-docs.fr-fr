---
title: Élément CommandPlacement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43fd417c4d54c0ab57133cf6dbff2c770c1ffc45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184337"
---
# <a name="commandplacement-element"></a>Élément CommandPlacement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’élément CommandPlacement permet de boutons, des groupes et des menus être inclus dans plus d’un groupe ou un menu. À l’aide de l’élément CommandPlacement, il est inutile de redéfinir intégralement ces éléments afin de modifier l’apparence d’une interface utilisateur.  
  
 Pour plus d’informations, consultez [création de groupes réutilisable de boutons](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Requis. Le guid du jeu de commandes, tel que défini dans le [élément Symbols](../extensibility/symbols-element.md).|  
|id|Requis. L’id du menu, un groupe ou une commande à placer, tel que défini dans le `Symbols Element`.|  
|priority|Requis. Détermine la position visuelle de l’élément dans son élément parent.|  
|Condition|facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent|Requis. Le menu ou un groupe qui héberge l’élément à être placé.|  
  
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
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
