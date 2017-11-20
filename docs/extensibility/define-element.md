---
title: "Définir l’élément | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b435c4e44391bbf477ed94fa96ee382613290530
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="define-element"></a>Définir l’élément
Définit une paire nom / valeur de symbole. Ce symbole peut être évalué par des attributs conditionnels. Pour plus d’informations, consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md). Voir aussi la [symboles élément](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Obligatoire. Le nom du symbole :<br /><br /> nom = « Mode »|  
|valeur|Obligatoire. La valeur du symbole :<br /><br /> valeur = « Standard »|  
|Condition|Facultatif. Pour plus d’informations, consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes par un VSPackage à l’environnement de développement intégré (IDE). Par exemple, des éléments de menu, menus, barres d’outils et zones de liste déroulante.|  
  
## <a name="example"></a>Exemple  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)