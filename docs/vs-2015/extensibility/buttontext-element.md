---
title: Élément ButtonText | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5ec72ffd7d0cc96b1ce66098efcfbda4fc30390
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255331"
---
# <a name="buttontext-element"></a>Élément ButtonText
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce champ vous permet de spécifier le texte qui apparaît dans différents menus. Par défaut, le `ButtonText` élément apparaît dans les contrôleurs de menu. Le `ButtonText` élément devient également la valeur par défaut si les autres champs de texte sont vides. Le `ButtonText` élément ne peut pas être vide, même si les autres champs de texte sont spécifiées.  
  
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
 La valeur de texte de la `ButtonText` élément fournit le texte qui est affiché pour les éléments de menu, combinés et autres éléments d’interface (UI) dont le texte visible.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

