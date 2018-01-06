---
title: "Élément de IDSymbol | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 004b40acb50fe85604d0a3cfa9f5626891fa66a4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idsymbol-element"></a>Élément de IDSymbol
Le `IDSymbol` élément contient l’ID de la paire GUID : ID qui représente un menu, un groupe ou une commande. Le GUID est fourni à partir du parent `GuidSymbol` élément. Le `IDSymbol` élément a un `name` attribut qui fournit un nom convivial pour l’ID, qui est contenue dans le `value` attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Obligatoire. Nom du symbole ID.|  
|par défaut|Obligatoire. Valeur d’ID numérique du symbole ID.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément GuidSymbol](../extensibility/guidsymbol-element.md)|Contient le GUID de la paire GUID : ID qui représente un menu, un groupe ou une commande. Groupe les éléments `IDSymbol`.|  
  
## <a name="remarks"></a>Notes  
 Chaque `IDSymbol` élément dans une donnée `GuidSymbol` l’élément doit avoir une valeur unique `value`. Toutefois, `IDSymbol` les éléments qui ont des valeurs identiques peuvent exister dans un package tant qu’ils disposent des parents différents.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)