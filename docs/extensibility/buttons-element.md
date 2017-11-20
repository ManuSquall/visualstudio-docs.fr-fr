---
title: "Boutons d’élément | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b2933f82c4088735f4203d947bad66c71aeb3e1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="buttons-element"></a>Élément de boutons
Groupes [bouton](../extensibility/button-element.md) éléments qui représentent des commandes individuelles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Buttons>  
  <Button>... </Button>  
  <Button>... </Button>  
</Buttons>  
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
|[Élément Buttons](../extensibility/buttons-element.md)|Regroupe les éléments de bouton.|  
|[Élément Button](../extensibility/button-element.md)|Définit une commande que l’utilisateur peut interagir avec.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Commands](../extensibility/commands-element.md)|Représente la collection de commandes dans la barre d’outils du VSPackage.|  
  
## <a name="example"></a>Exemple  
  
```  
<Buttons>  
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">  
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>  
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>  
    <Strings>  
      <ButtonText>C# Command Sample</ButtonText>  
    </Strings>  
  </Button>  
</Buttons>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les VSPackages ajouter les éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)