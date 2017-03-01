---
title: La Structure du fichier [Content_types] .xml | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 6f45707a88a27fa54840825d9562f859385ce4b7
ms.lasthandoff: 02/22/2017

---
# <a name="the-structure-of-the-contenttypesxml-file"></a>La Structure du fichier [Content_types] .xml
Contient des informations sur les types de contenu dans un package VSIX. Visual Studio utilise le fichier [Content_Types] .xml pour installer le package, mais il n’installe pas le fichier lui-même.  
  
> [!NOTE]
>  Bien que cette rubrique s’applique uniquement aux fichiers [Content_Type] .xml qui sont utilisés dans les packages VSIX, le type de fichier [Content_Types] .xml fait partie de la *Open Packaging Conventions (OPC)* standard. Pour plus d’informations, consultez [OPC : une nouvelle norme pour l’empaquetage de vos données](http://go.microsoft.com/fwlink/?LinkID=148207) sur le site Web MSDN.  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent l’élément racine et de ses attributs et éléments enfants.  
  
### <a name="root-element"></a>Élément racine  
  
|Élément|Description|  
|-------------|-----------------|  
|`Types`|Contient des éléments enfants qui énumèrent les types de fichiers dans le package VSIX.|  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Xmlns`|(Obligatoire.) L’emplacement du schéma utilisé pour ce fichier [Content_Types] .xml.|  
  
### <a name="attribute-name-attribute"></a>{Nom de l’attribut} Attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|http://schemas.OpenFormats.org/package/2006/Content-types|L’emplacement du schéma des types de contenu.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Le `Types` élément peut contenir un nombre quelconque de `Default` éléments.  
  
|Élément|Description|  
|-------------|-----------------|  
|`Default`|Décrit un type de contenu dans le package VSIX. Chaque type de fichier dans le package doit avoir son propre `Default` élément.|  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Extension`|L’extension de nom de fichier d’un fichier dans le package VSIX.|  
|`ContentType`|Décrit le type de contenu qui est associé à l’extension de nom de fichier.|  
  
### <a name="attribute-name-attribute"></a>{Nom de l’attribut} Attribut  
 Visual Studio reconnaît les symboles suivants `ContentType` valeurs associé au `Extension` types.  
  
|Extension|ContentType|  
|---------------|-----------------|  
|txt|texte brut|  
|pkgdef|texte brut|  
|xml|texte/xml|  
|vsixmanifest|texte/xml|  
|htm ou html|texte/html|  
|RTF|application/rtf|  
|PDF|application/pdf|  
|GIF|image/gif|  
|jpg ou jpeg|image/jpg|  
|TIFF|image/tiff|  
|vsix|application/zip|  
|ZIP|application/zip|  
|dll|application/octet-stream|  
|tous les autres types de fichiers|application/octet-stream|  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Le fichier [Content_Types] .xml suivant décrit un package VSIX standard.  
  
### <a name="code"></a>Code  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Référence du schéma 1.0 Extension VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC : Une nouvelle norme pour l’empaquetage de vos données](http://go.microsoft.com/fwlink/?LinkID=148207)
