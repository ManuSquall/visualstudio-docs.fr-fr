---
title: "Élément de GuidSymbol | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d5089d87156bd5eb191176fe73ab19a01d497b90
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="guidsymbol-element"></a>Élément de GuidSymbol
Le `GuidSymbol` élément contient le GUID de la paire GUID : ID qui représente un menu, un groupe ou une commande. L’ID provient d’un `IDSymbol` élément dans le `GuidSymbol` élément. Le `GuidSymbol` élément a un `name` attribut qui fournit un nom convivial pour le GUID, qui est contenu dans le `value` attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Obligatoire. Nom du symbole GUID.|  
|par défaut|Obligatoire. GUID du symbole GUID.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément IDSymbol](../extensibility/idsymbol-element.md)|Contient l’ID de la paire GUID : ID qui représente un menu, un groupe ou une commande.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Symbols](../extensibility/symbols-element.md)|Groupes `GuidSymbol` éléments dans un fichier .vsct.|  
  
## <a name="remarks"></a>Notes  
 En règle générale, un fichier .vsct contient trois `GuidSymbol` éléments dans son `Symbols` section, l’autre pour le package lui-même, un pour le jeu de commandes (la collection de menus, les groupes et les commandes que le package met à disposition) et un pour les bitmaps qui fournissent des icônes pour les boutons et autres composants visuels. Chaque `IDSymbol` élément dans une donnée `GuidSymbol` l’élément doit avoir une valeur unique `value`. Toutefois, `IDSymbol` les éléments qui ont des valeurs identiques peuvent exister dans un package tant qu’ils disposent des parents différents.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)