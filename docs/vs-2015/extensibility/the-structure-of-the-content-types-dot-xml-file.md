---
title: La structure du fichier Content_types]. Xml | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d6eca44c08cf35e7b2075965c1b6139e7fb95bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395358"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Structure du fichier Content_types].xml
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contient des informations sur les genres de contenu dans un package VSIX. Visual Studio utilise le fichier [Content_Types]. xml pour installer le package, mais il n’installe pas le fichier lui-même.  
  
> [!NOTE]
> Bien que cette rubrique s’applique uniquement aux fichiers [Content_Type]. XML utilisés dans les packages VSIX, le type de fichier [Content_Types]. xml fait partie de la norme *OPC (Open Packaging Conventions)* . Pour plus d’informations, consultez [OPC : nouvelle norme pour l’empaquetage de vos données](https://msdn.microsoft.com/magazine/cc163372.aspx) sur le site Web MSDN.  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent l’élément racine et ses attributs et éléments enfants.  
  
### <a name="root-element"></a>Élément racine  
  
|Élément|Description|  
|-------------|-----------------|  
|`Types`|Contient des éléments enfants qui énumèrent les types de fichiers dans le package VSIX.|  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Xmlns`|(Obligatoire.) Emplacement du schéma utilisé pour ce fichier [Content_Types]. Xml.|  
  
### <a name="attribute-name-attribute"></a>{Nom de l’attribut} Attribut  
  
|                           Valeur                           |                Description                |
|-----------------------------------------------------------|-------------------------------------------|
| `http://schemas.openformats.org/package/2006/content-types` | Emplacement du schéma des types de contenu. |
  
### <a name="child-elements"></a>Éléments enfants  
 L'élément `Types` peut contenir un nombre illimité d'éléments `Default`.  
  
|Élément|Description|  
|-------------|-----------------|  
|`Default`|Décrit un type de contenu dans le package VSIX. Chaque type de fichier du package doit avoir son propre `Default` élément.|  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Extension`|Extension de nom de fichier d’un fichier dans le package VSIX.|  
|`ContentType`|Décrit le type de contenu associé à l’extension de nom de fichier.|  
  
### <a name="attribute-name-attribute"></a>{Nom de l’attribut} Attribut  
 Visual Studio reconnaît les `ContentType` valeurs suivantes pour les `Extension` types associés.  
  
|Extension|ContentType|  
|---------------|-----------------|  
|txt|texte/brut|  
|fichier pkgdef|texte/brut|  
|Xml|text/xml|  
|vsixmanifest|text/xml|  
|htm ou html|texte/html|  
|RTF|application/RTF|  
|pdf|application/pdf|  
|GIF|image/gif|  
|jpg ou JPEG|image/jpg|  
|tiff|image/tiff|  
|vsix|application/zip|  
|zip|application/zip|  
|dll|application/octet-stream|  
|tous les autres types de fichiers|application/octet-stream|  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Le fichier [Content_Types]. XML suivant décrit un package VSIX classique.  
  
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
 [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Informations de référence sur le schéma d’extension VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC : nouvelle norme pour l’empaquetage de vos données](https://msdn.microsoft.com/magazine/cc163372.aspx)
