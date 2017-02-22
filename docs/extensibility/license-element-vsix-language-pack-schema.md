---
title: "License, &#233;l&#233;ment (sch&#233;ma du module linguistique VSIX) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# License, &#233;l&#233;ment (sch&#233;ma du module linguistique VSIX)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Facultatif. Le chemin d'accès d'une version localisée du fichier de licence pour l'extension.  
  
## Syntaxe  
  
```  
<License>FilePath\license.txt</License>  
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
|None||  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[VSIXLanguagePack, élément](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obligatoire. Fournit l'élément racine pour un module linguistique VSIX.|  
  
## Valeur texte  
 Le chemin d'accès relatif du fichier de licence localisé à afficher.  
  
## Notes  
 Si le `License` élément est défini, puis le texte du fichier de licence désigné est affiché lors de l'installation et l'utilisateur doit accepter la licence à continuer.  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms|http:\/\/schemas.Microsoft.com\/Developer\/VSX\-Schema\-LP\/2010|  
|Nom du schéma|Schéma du module linguistique VSIX|  
|Fichier de validation|VSIXLanguagePackSchema.xsd|  
|Peut être vide|Non applicable|  
  
## Voir aussi  
 [Référence du schéma VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localisation de Packages VSIX](../extensibility/localizing-vsix-packages.md)   
 [Référence du schéma 1.0 Extension VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)