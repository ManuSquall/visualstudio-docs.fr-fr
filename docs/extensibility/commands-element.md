---
title: "Commandes d’élément | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7c5cce390ad786ad530153e1850850509990b039
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="commands-element"></a>Élément Commands
Représente la collection de commandes dans la barre d’outils du VSPackage. La collection peut avoir jusqu'à cinq sous-sections, comme suit : menus, les groupes, les boutons, combinés et les bitmaps.  
  
 Chaque élément enfant sous-section, par exemple, \<Menu >, est identifié par un ID de commande unique qui est un GUID et une paire de l’identificateur numérique. Le GUID identifie le jeu de commandes « » et est utilisé pour regrouper les commandes logiquement associées. Le VSPackage doit définir son propre ensemble pour éviter les conflits avec les ID de commande qui sont définis par d’autres packages VS de commandes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|package|GUID qui identifie le package Visual Studio qui fournit les commandes.<br /><br /> Par exemple, un package = « guidVsPackage1Pkg ».|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Menus](../extensibility/menus-element.md)|Définit tous les menus un VSPackage implémente.|  
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commandes dans un VSPackage.|  
|[Élément Buttons](../extensibility/buttons-element.md)|Regroupe les éléments de bouton.|  
|[Élément Bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments d’image Bitmap.|  
|[Élément Combos](../extensibility/combos-element.md)|Regroupe les éléments de liste déroulante.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes par un VSPackage à l’IDE. Éléments possibles sont les éléments de menu, des menus, des barres d’outils et des zones de liste déroulante.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser un [élément Commands](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage">  
    <Menus>  
      <Menu Condition="'%(DEBUG)' != 'true'"   
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"   
        priority="0x0000" type="Menu">  
        <Annotation>  
          <Documentation>this is an annotation</Documentation>  
          <AppInfo>  
            <CustomData>  
              <CustomSubElement>Some data</CustomSubElement>  
            </CustomData>  
          </AppInfo>  
        </Annotation>  
        <CommandFlag>AlwaysCreate</CommandFlag>  
        <Strings>  
          <ButtonText>MainMenu</ButtonText>  
        </Strings>  
      </Menu>  
  </Menus>  
<Commands>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les VSPackages ajouter les éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)