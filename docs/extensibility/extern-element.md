---
title: "&#201;l&#233;ment de extern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Extern"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, Extern"
  - "Élément extern (schéma XML de VSCT)"
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# &#201;l&#233;ment de extern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément Extern fait référence à tous les fichiers externes en\-tête \(.h\) à fusionner avec le fichier .vsct au moment de la compilation. Les fichiers devant être fusionnées doivent être sur le chemin d'accès Include fourni au compilateur VSCT ou référencé par une [Élément Include](../extensibility/include-element.md). Les fichiers peuvent être des autres fichiers .vsct ou les fichiers d'en\-tête C\+\+.  
  
 Définitions des fichiers d'en\-tête doivent être sous la forme « \#define \[symbole\] \[valeur\] » la valeur peut être un autre symbole si elle est déjà définie. Les définitions peuvent servir dans les instructions conditionnelles des éléments de commande. Les symboles ne sont pas utilisés seront ignorées.  
  
 CommandTable Element  
Extern Element  
  
## Syntaxe  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|href|Obligatoire. Le chemin d'accès au fichier d'en\-tête :<br /><br /> href\="stdidcmd.h »|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|language|Facultatif. La langue par défaut de tous les [\< chaînes \>](../extensibility/strings-element.md) des éléments de la table de commande :<br /><br /> Language \= "en\-us »|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun|Aucun.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes, autrement dit, les éléments de menu, menus, barres d'outils et des zones de liste déroulante, assurant un VSPackage à l'IDE.|  
  
## Exemple  
  
```  
<?xml version="1.0" encoding="utf-8"?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10- 18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema"> <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/> … <Commands package="guidMyPackage"> </CommandTable>  
```  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)