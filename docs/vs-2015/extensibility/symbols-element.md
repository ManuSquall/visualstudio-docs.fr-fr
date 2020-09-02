---
title: Symbols, élément | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8d28d225bd3a8d5c105bf54b9c63574002aed15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160461"
---
# <a name="symbols-element"></a>Élément Symbols
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Définit les GUID et les ID utilisés par d’autres éléments VSCT. Pour le code non managé, ces informations proviennent généralement des fichiers d’en-tête spécifiés par l' [élément extern](../extensibility/extern-element.md). Le code managé utilise les éléments enfants de l’élément Symbols pour définir ces informations.  
  
 Si vous créez un fichier. vsct à partir d’un fichier. directeur de la génération existante, les symboles sont générés en tant qu’enfants de l’élément Symbols. Pour plus d’informations, consultez [Comment : créer un. Fichier vsct à partir d’un existant. Fichier de directeur technique](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 L’élément Symbols ne doit pas être confondu avec l' [élément define](../extensibility/define-element.md), qui définit des paires nom-valeur pour une utilisation par le préprocesseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|None||  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|GuidSymbol|Définit un symbole GUID. GuidSymbol a deux attributs obligatoires : Name et value. Le nom est le nom du symbole et la valeur est la valeur du GUID sous la forme d’une chaîne.<br /><br /> Par exemple :\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|  
|IDSymbol|Définit un symbole. IDSymbol a deux attributs obligatoires : Name et value. Le nom est le nom du symbole et la valeur est la valeur du symbole sous la forme d’une chaîne.<br /><br /> Par exemple :\<IDSymbol name="MyMenuGroup" value="0x1020" />|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Élément racine du fichier. vsct.|  
  
## <a name="example"></a> Exemple  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
