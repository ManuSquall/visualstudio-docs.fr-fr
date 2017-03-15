---
title: "D&#233;finir l&#39;&#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, définir"
  - "Définir l'élément (schéma XML de VSCT)"
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# D&#233;finir l&#39;&#233;l&#233;ment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit une paire nom \/ valeur de symbole. Ce symbole peut être évalué par des attributs conditionnels. Pour plus d'informations, consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md). Consultez également la [Élément de symboles](../extensibility/symbols-element.md).  
  
## Syntaxe  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Obligatoire. Le nom du symbole :<br /><br /> nom \= « Mode »|  
|valeur|Obligatoire. La valeur du symbole :<br /><br /> valeur \= « Standard »|  
|Condition|Facultatif. Pour plus d'informations, consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes qui fournit un VSPackage à l'environnement de développement intégré \(IDE\). Par exemple, des éléments de menu, menus, barres d'outils et zones de liste déroulante.|  
  
## Exemple  
  
```  
<Define name="DEMO_UI"/> <Define name="MODE" value="Standard"/>  
```  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)