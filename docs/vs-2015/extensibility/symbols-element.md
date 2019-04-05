---
title: Symboles d’élément | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951415"
---
# <a name="symbols-element"></a>Élément Symbols
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Définit le GUID et ID qui sont utilisés par d’autres éléments VSCT. Du code non managé, ces informations proviennent généralement des fichiers d’en-tête qui sont spécifiées par [élément Extern](../extensibility/extern-element.md). Le code managé utilise les éléments enfants de l’élément de symboles pour définir ces informations.  
  
 Si vous créez un fichier .vsct à partir d’un fichier .cto existant, les symboles seront générés en tant qu’enfants de l’élément de symboles. Pour plus d'informations, voir [Procédure : Créer un. Fichier VSCT d’un existant. Fichier de directeur technique](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 L’élément de symboles ne doit pas être confondu avec le [définir un élément](../extensibility/define-element.md), qui définit les paires nom-valeur pour une utilisation par le préprocesseur.  
  
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
|Aucun.||  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|GuidSymbol|Définit un symbole GUID. GuidSymbol possède deux attributs requis : nom / valeur. Le nom est le nom du symbole, et la valeur est la valeur du GUID sous forme de chaîne.<br /><br /> For example:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|  
|IDSymbol|Définit un symbole. IDSymbol possède deux attributs requis : nom / valeur. Le nom est le nom du symbole, et la valeur est la valeur du symbole sous forme de chaîne.<br /><br /> For example:\<IDSymbol name="MyMenuGroup" value="0x1020" />|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|L’élément racine du fichier .vsct.|  
  
## <a name="example"></a>Exemple  
  
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
