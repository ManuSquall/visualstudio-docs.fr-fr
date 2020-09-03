---
title: Définir l’élément | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cc543a07176f307641c53a2ef3e132881821ce7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162155"
---
# <a name="define-element"></a>Élément Define
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Définit un nom de symbole et une paire de valeurs. Ce symbole peut être évalué par des attributs conditionnels. Pour plus d’informations, consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md). Voir aussi l' [élément Symbols](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Obligatoire. Nom du symbole :<br /><br /> Name = "mode"|  
|value|Obligatoire. Valeur du symbole :<br /><br /> valeur = « standard »|  
|Condition|facultatif. Pour plus d’informations, consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent les commandes qu’un VSPackage fournit à l’environnement de développement intégré (IDE). Par exemple, les éléments de menu, les menus, les barres d’outils et les zones de liste modifiable.|  
  
## <a name="example"></a> Exemple  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
