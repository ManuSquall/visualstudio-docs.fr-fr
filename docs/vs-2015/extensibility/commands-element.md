---
title: Commands, élément | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 194768a3b540511996e1d99e6450a7a9b24ebc74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184296"
---
# <a name="commands-element"></a>Élément Commands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Représente la collection de commandes dans la barre d’outils VSPackage. La collection peut contenir jusqu’à cinq sous-sections, comme suit : menus, groupes, boutons, combos et bitmaps.  
  
 Chaque élément enfant de sous-section, par exemple, \<Menu> est identifié par un ID de commande unique qui est un GUID et une paire d’identificateurs numériques. Le GUID identifie le « jeu de commandes » et est utilisé pour regrouper les commandes associées de manière logique. Le VSPackage doit définir son propre jeu de commandes pour éviter les collisions avec les ID de commande définis par d’autres VSPackages.  
  
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
|package|GUID qui identifie le VSPackage qui fournit les commandes.<br /><br /> Par exemple, package = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Menus](../extensibility/menus-element.md)|Définit tous les menus qu’un VSPackage implémente.|  
|[Élément Groups](../extensibility/groups-element.md)|Contient des entrées qui définissent les groupes de commandes dans un VSPackage.|  
|[Élément Buttons](../extensibility/buttons-element.md)|Éléments du bouton groupes.|  
|[Élément Bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments bitmap.|  
|[Élément Combos](../extensibility/combos-element.md)|Regroupe les éléments de liste.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes qu’un VSPackage fournit à l’IDE. Les éléments possibles sont les éléments de menu, les menus, les barres d’outils et les zones de liste modifiable.|  
  
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
 [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
