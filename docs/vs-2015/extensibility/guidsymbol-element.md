---
title: Élément GuidSymbol | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204219"
---
# <a name="guidsymbol-element"></a>Élément GuidSymbol
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' `GuidSymbol` élément contient le GUID de la paire GUID : ID qui représente un menu, un groupe ou une commande. L’ID provient d’un `IDSymbol` élément dans l' `GuidSymbol` élément. L' `GuidSymbol` élément a un `name` attribut qui fournit un nom convivial pour le GUID, qui est contenu dans l' `value` attribut.  
  
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
|value|Obligatoire. GUID du symbole GUID.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément IDSymbol](../extensibility/idsymbol-element.md)|Contient l’ID de la paire GUID : ID qui représente un menu, un groupe ou une commande.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Symbols](../extensibility/symbols-element.md)|Regroupe les `GuidSymbol` éléments dans un fichier. vsct.|  
  
## <a name="remarks"></a>Notes  
 En règle générale, un fichier. vsct contient trois `GuidSymbol` éléments dans sa `Symbols` section, l’un pour le package lui-même, l’autre pour le jeu de commandes (la collection de menus, les groupes et les commandes que le package rend disponibles) et l’autre pour les bitmaps qui fournissent des icônes pour les boutons et autres composants visuels. Chaque `IDSymbol` élément d’un `GuidSymbol` élément donné doit avoir un unique `value` . Toutefois, les `IDSymbol` éléments qui ont des valeurs identiques peuvent exister dans un package, à condition qu’ils aient des parents différents.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
