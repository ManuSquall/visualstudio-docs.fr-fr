---
title: "VSIXLanguagePack, &#233;l&#233;ment (sch&#233;ma du module linguistique VSIX) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# VSIXLanguagePack, &#233;l&#233;ment (sch&#233;ma du module linguistique VSIX)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obligatoire. Fournit l'élément racine pour un module linguistique VSIX. Le module linguistique VSIX fournit des informations d'installation localisé pour un package VSIX.  
  
## Syntaxe  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`xmlns`|L'espace de noms XML dans lequel le schéma du module linguistique VSIX est défini.|  
  
## xmlns attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Obligatoire. L'emplacement du fichier qui définit le schéma pour les modules linguistiques.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[LocalizedName, élément](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Obligatoire. Le nom localisé de l'extension à installer.|  
|[LocalizedDescription, élément](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Obligatoire. Description localisée de l'extension à installer.|  
|[MoreInfoURL, élément](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Facultatif. Un lien vers les informations localisées sur l'extension.|  
|[Élément de licence](../extensibility/license-element-vsix-language-pack-schema.md)|Facultatif. Le chemin d'accès d'une version localisée du fichier de licence pour l'extension.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun||  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms|http:\/\/schemas.Microsoft.com\/Developer\/VSX\-Schema\-LP\/2010|  
|Nom du schéma|Schéma du module linguistique VSIX|  
|Fichier de validation|VSIXLanguagePackSchema.xsd|  
|Peut être vide|Non|  
  
## Voir aussi  
 [Référence du schéma VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localisation de Packages VSIX](../extensibility/localizing-vsix-packages.md)   
 [Référence du schéma 1.0 Extension VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)