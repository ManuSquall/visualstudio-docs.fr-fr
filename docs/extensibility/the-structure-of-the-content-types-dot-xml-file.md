---
title: La structure du fichier [Content_types].xml (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 957958cd930620734d09c592ea07bfb0919d0145
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395314"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Structure du fichier [Content_types].xml
Contient des informations sur les types de contenu dans un paquet VSIX. Visual Studio utilise le fichier [Content_Types].xml pour installer le paquet, mais il n’installe pas le fichier lui-même.

> [!NOTE]
> Bien que ce sujet ne s’applique qu’aux fichiers [Content_Type].xml qui sont utilisés dans les paquets VSIX, le type de fichier [Content_Types].xml fait partie de la norme *Des conventions d’emballage ouvert (CPVP).* Pour plus d’informations, voir [OPC: A New Standard For Packaging Your Data](https://msdn.microsoft.com/magazine/cc163372.aspx) sur le site Web msDN.

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent l’élément racine et ses attributs et les éléments pour enfants.

### <a name="root-element"></a>Élément racine

|Élément|Description|
|-------------|-----------------|
|`Types`|Contient des éléments pour enfants qui énumèrent les types de fichiers dans le paquet VSIX.|

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Xmlns`|(Requis.) L’emplacement du schéma utilisé pour ce fichier [Content_Types].xml.|

### <a name="attribute-name-attribute"></a>Nom d’attribut Attribut

| Valeur | Description |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | L’emplacement du schéma des types de contenu. |

### <a name="child-elements"></a>Éléments enfants
 L'élément `Types` peut contenir un nombre illimité d'éléments `Default`.

|Élément|Description|
|-------------|-----------------|
|`Default`|Décrit un type de contenu dans le paquet VSIX. Chaque type de fichier dans `Default` le paquet doit avoir son propre élément.|

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Extension`|L’extension du nom de fichier d’un fichier dans le paquet VSIX.|
|`ContentType`|Décrit le type de contenu associé à l’extension du nom de fichier.|

### <a name="attribute-name-attribute"></a>Nom d’attribut Attribut
 Visual Studio reconnaît `ContentType` les valeurs `Extension` suivantes pour les types associés.

|Extension|ContentType|
|---------------|-----------------|
|txt|texte/brut|
|pkgdef (pkgdef)|texte/brut|
|Xml|text/xml|
|vsixmanifest (en)|text/xml|
|htm ou html|texte/html|
|Rtf|application/rtf|
|pdf|application/pdf|
|GIF|image/gif|
|jpg ou jpeg|image/jpg|
|tiff|image/tiff|
|vsix|application/zip|
|zip|application/zip|
|dll|application/octet-stream|
|tous les autres types de fichiers|application/octet-stream|

## <a name="example"></a>Exemple

### <a name="description"></a>Description
 Le fichier suivant [Content_Types].xml décrit un paquet VSIX typique.

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
- [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [VSIX Extension Schema 1.0 Référence](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC : une nouvelle norme pour l’emballage de vos données](https://msdn.microsoft.com/magazine/cc163372.aspx)