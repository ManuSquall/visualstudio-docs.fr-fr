---
title: "&#201;l&#233;ment de symboles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Élément de symboles (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, symboles"
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# &#201;l&#233;ment de symboles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit le GUID et ID qui sont utilisés par d'autres éléments VSCT. Du code non managé, cette information provient généralement des fichiers d'en\-tête spécifiés par [Élément de extern](../extensibility/extern-element.md). Le code managé utilise les éléments enfants de l'élément de symboles pour définir ces informations.  
  
 Si vous créez un fichier .vsct à partir d'un fichier .cto existant, les symboles seront générés en tant qu'enfants de l'élément de symboles. Pour plus d'informations, consultez [Comment : créer un fichier .Vsct à partir d’un fichier .Cto existant](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md).  
  
 L'élément de symboles ne doit pas être confondu avec le [Définir l'élément](../extensibility/define-element.md), qui définit les paires nom\-valeur pour une utilisation par le préprocesseur.  
  
## Syntaxe  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|None||  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|GuidSymbol|Définit un symbole GUID. GuidSymbol possède deux attributs requis : nom et valeur. Le nom est le nom du symbole et la valeur est la valeur du GUID sous forme de chaîne.<br /><br /> Par exemple : \< GuidSymbol nom \= valeur de « guidVsPackage1Pkg » \= "{c5f54698\-101a\-4846\-84d3\-dc748f9cd848}" \/ \>|  
|IDSymbol|Définit un symbole. IDSymbol possède deux attributs requis : nom et valeur. Le nom est le nom du symbole et la valeur est la valeur du symbole sous forme de chaîne.<br /><br /> Par exemple : \< IDSymbol nom \= valeur de « MyMenuGroup » \= « 0x1020 » \/ \>|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de CommandTable](../extensibility/commandtable-element.md)|L'élément racine du fichier .vsct.|  
  
## Exemple  
  
```  
<Symbols> <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" /> <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="cmdidMyCommand" value="0x0100" /> <IDSymbol name="cmdidMyTool" value="0x0101" /> </GuidSymbol> </Symbols>  
```  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)