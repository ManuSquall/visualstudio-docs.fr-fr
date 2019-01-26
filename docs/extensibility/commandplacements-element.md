---
title: Élément CommandPlacements | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923ba2a517ae934fb83c0cb36a29dbe518a2a2a3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991058"
---
# <a name="commandplacements-element"></a>Élément CommandPlacements
L’élément CommandPlacements regroupe les éléments CommandPlacement et autres regroupements CommandPlacements.  
  
 L’élément CommandPlacements est facultatif. Si aucun commandes, les groupes ou les menus ne doivent être inclus dans un emplacement secondaire, il est inutile d’inclure cette section dans votre *.vsct* fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
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
|CommandPlacements|Regroupe les éléments CommandPlacement et autres regroupements CommandPlacements.|  
|[Élément CommandPlacement](../extensibility/commandplacement-element.md)|Active les boutons, des groupes et des menus être inclus dans plus d’un groupe ou un menu.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes.|  
  
## <a name="example"></a>Exemple  
  
```xml  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CommandPlacement](../extensibility/commandplacement-element.md)   
 [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)