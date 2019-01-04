---
title: Élément ButtonText | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 8edd12a2f37ea0de3a3c01f013adea64a08424f5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905583"
---
# <a name="buttontext-element"></a>Élément ButtonText
Ce champ vous permet de spécifier le texte qui apparaît dans différents menus. Par défaut, le `ButtonText` élément apparaît dans les contrôleurs de menu. Le `ButtonText` élément devient également la valeur par défaut si les autres champs de texte sont vides. Le `ButtonText` élément ne peut pas être vide, même si les autres champs de texte sont spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
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
 La valeur de texte de la `ButtonText` élément fournit le texte qui est affiché pour les éléments de menu, combinés et autres éléments d’interface (UI) dont le texte visible.  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)