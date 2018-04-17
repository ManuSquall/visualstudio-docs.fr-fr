---
title: Élément de ButtonText | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2fca0fbb22bf51353eeaa64f519face53bfb23c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="buttontext-element"></a>Élément de ButtonText
Ce champ permet de spécifier le texte qui apparaît dans différents menus. Par défaut, le `ButtonText` élément apparaît dans les contrôleurs de menu. Le `ButtonText` élément devient également la valeur par défaut si les autres champs de texte sont vides. Le `ButtonText` élément ne peut pas être vide même si les autres champs de texte sont spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Strings](../extensibility/strings-element.md)|Regroupe les éléments de texte, tel que `ButtonText` et `CommandName`.|  
  
## <a name="text-value"></a>Valeur texte  
 La valeur de texte de la `ButtonText` élément fournit le texte qui est affiché pour les éléments de menu, combinés et autres éléments d’interface (interface utilisateur) qui contiennent le texte visible.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)