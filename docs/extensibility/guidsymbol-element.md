---
title: Élément GuidSymbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 16e7a1b84a6baa26b69545b3fa55e4434e5998f3
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500067"
---
# <a name="guidsymbol-element"></a>Élément GuidSymbol
Le `GuidSymbol` élément contient le GUID de la paire GUID : ID qui représente un menu, un groupe ou une commande. L’ID provient d’un `IDSymbol` élément dans le `GuidSymbol` élément. Le `GuidSymbol` élément a un `name` attribut qui fournit un nom convivial pour le GUID, qui est contenu dans le `value` attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
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
|[Élément Symbols](../extensibility/symbols-element.md)|Groupes `GuidSymbol` éléments dans un *.vsct* fichier.|  
  
## <a name="remarks"></a>Notes  
 En règle générale, un *.vsct* fichier contient trois `GuidSymbol` éléments dans son `Symbols` section, un pour le package lui-même, un pour le jeu de commandes (la collection de menus, des groupes et commandes que le package rend disponible), et une pour les bitmaps qui fournissent des icônes pour les boutons et autres composants visuels. Chaque `IDSymbol` élément dans une donnée `GuidSymbol` élément doit avoir une valeur unique `value`. Toutefois, `IDSymbol` les éléments qui ont des valeurs identiques peuvent exister dans un package, à condition qu’ils disposent des parents différents.  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)