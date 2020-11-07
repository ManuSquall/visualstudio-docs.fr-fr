---
title: Cache de schéma de l’éditeur XML
description: En savoir plus sur le cache de schéma fourni par l’éditeur XML qui comprend les schémas XML standard utilisés pour IntelliSense et la validation de document XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3eaab4379d744bae0032e51995e5bc1b8e76423
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351373"
---
# <a name="schema-cache"></a>Cache de schéma

L’éditeur XML fournit un cache de schéma situé dans le répertoire *%VSInstallDir%\xml\Schemas* . Le cache de schéma est global pour tous les utilisateurs sur votre ordinateur et comprend des schémas XML standard qui sont utilisés pour IntelliSense et la validation de document XML.

L’éditeur XML peut également trouver des schémas situés dans la solution, des schémas spécifiés dans le champ **schémas** de la fenêtre **Propriétés** du document et des schémas identifiés par les `xsi:schemaLocation` `xsi:noNamespaceSchemaLocation` attributs et.

Le tableau suivant décrit les schémas installés avec l’éditeur XML.

| Nom de fichier | Description |
|-| - |
| *catalog.xsd* | Schéma pour des fichiers catalogue de schémas de l'éditeur XML. Pour des informations sur les catalogues de schémas, voir ci-dessous. |
| *DotNetConfig.xsd* | Schéma pour les fichiers Web.Config, `http://schemas.microsoft.com/.NETConfiguration/v2.0` . |
| *msbuild.xsd* | Schéma pour les fichiers Make de MSBuild, `http://schemas.microsoft.com/developer/msbuild/2003` . |
| *msdata.xsd* | Schéma pour les annotations XSD ajoutées par la classe <xref:System.Data.DataSet>, « urn:schemas-microsoft-com:xml-msdata ». |
| *msxsl.xsd* | Schéma pour les extensions de bloc de script Microsoft XSLT, urn:schemas-microsoft-com:xslt. |
| *SnippetFormat.xsd* | Schéma pour les fichiers XML d'extrait de code. Pour obtenir des exemples, consultez *%VSInstallDir%\VC # \Expansions*. |
| *Soap1.1.xsd* | Schéma pour le protocole SOAP (Simple Object Access Protocol) 1,1, `http://schemas.xmlsoap.org/soap/envelope/` . |
| *Soap1.2.xsd* | Schéma pour Simple Object Access Protocol 1.2. |
| *SiteMapSchema.xsd* | Schéma pour le fichier XML Sitemap ASP.NET, `http://schemas.microsoft.com/AspNet/SiteMap-File-1.0` . |
| *wsdl.xsd* | Schéma pour le langage de description de service Web, `http://schemas.xmlsoap.org/wsdl/` . |
| *xenc.xsd* | Schéma pour le chiffrement XML, `http://www.w3.org/2000/09/xmldsig#` . |
| *xhtml.xsd* | Schéma pour XHTML `http://www.w3.org/1999/xhtml` . |
| *xlink.xsd* | Schéma pour XLink 1.0, `http://www.w3.org/1999/xlink` . |
| *xml.xsd* | Schéma décrivant les attributs XML : Space et XML : lang, `http://www.w3.org/XML/1998/namespace` . |
| *xmlsig.xsd* | Schéma pour les signatures numériques XML, `http://www.w3.org/2000/09/xmldsig#` . |
| *xsdschema.xsd* | Schéma décrivant XSD lui-même, `http://www.w3.org/2001/XMLSchema` . |
| *xslt.xsd* | Schéma pour les transformations XML, `http://www.w3.org/1999/XSL/Transform` . |

## <a name="update-schemas-in-the-cache"></a>Mettre à jour les schémas dans le cache

L'éditeur charge le répertoire de cache de schéma lors du chargement du package de l'éditeur XML et contrôle si des modifications ont été apportées pendant l'exécution. Si un schéma a été ajouté, il est automatiquement chargé dans un index en mémoire des schémas connus. Si un schéma a été supprimé, il est automatiquement effacé de l'index en mémoire. Si un schéma a été mise à jour, il invalide automatiquement le cache en mémoire de ce schéma.

> [!NOTE]
> Étant donné que le répertoire de cache de schéma est global sur votre ordinateur, n'y ajoutez que des schémas standard et utiles pour tous les projets Visual Studio susceptibles d'être créés sur votre ordinateur.

L'éditeur XML prend également en charge un nombre quelconque de fichiers catalogue de schémas dans le répertoire de cache de schéma. Les catalogues de schémas peuvent pointer vers d'autres emplacements de schémas que l'éditeur doit toujours reconnaître. Le fichier *Catalog. xsd* définit le format du fichier catalogue et est inclus dans le répertoire de cache de schéma. Le fichier *catalog.xml* est le catalogue par défaut et il contient des liens vers d’autres schémas dans *% VSInstallDir%*. Voici un échantillon du fichier *catalog.xml* :

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%VSInstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

L’attribut `href` peut être n’importe quel chemin de fichier ou URL http pointant vers le schéma. Le chemin de fichier peut être relatif au document de catalogue. Les variables suivantes, délimitées par%%, sont reconnues par l’éditeur et développées dans le chemin d’accès :

- VSInstallDir

- Système

- ProgramFiles

- Programmes

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

Le document de catalogue peut contenir un élément `Catalog` pointant vers d'autres catalogues. Vous pouvez utiliser l'élément `Catalog` pour pointer vers un catalogue central partagé par votre équipe ou votre entreprise ou vers un catalogue en ligne partagé avec vos partenaires commerciaux. L’attribut `href` est le chemin de fichier ou l’URL http des autres catalogues. Voici un exemple d'élément `Catalog` :

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

Le catalogue peut également contrôler la façon dont les schémas sont associés aux documents XML à l'aide de l'élément spécial `Association`. Cet élément associe des schémas qui n’ont pas d’espace de noms cible avec une extension de fichier particulière, ce qui peut être utile car l’éditeur XML n’effectue aucune association automatique de schémas qui n’ont pas d' `targetNamespace` attribut. Dans l'exemple suivant, l'élément `Association` associe le schéma dotNetConfig à tous les fichiers dont l'extension est « config » :

```xml
<Association extension="config" schema="%VSInstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Schémas localisés

Dans de nombreux cas, le fichier *catalog.xml* ne contient pas d’entrées pour les schémas localisés. Vous pouvez ajouter des entrées supplémentaires au fichier *catalog.xml* qui pointent vers le répertoire de schéma localisé.

Dans l'exemple suivant, un nouvel élément `Schema` a été créé et il utilise la variable %LCID% pour pointer vers le schéma localisé.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Modifier l’emplacement du cache de schéma

Vous pouvez personnaliser l’emplacement du cache de schéma à l’aide de la page options **diverses** . Si vous avez un répertoire de schémas favoris, l'éditeur peut être configuré pour utiliser ces schémas au lieu de ceux par défaut.

> [!NOTE]
> Ce changement n'affecte que l'utilisateur actuel de Visual Studio.

### <a name="to-change-the-schema-cache-location"></a>Pour modifier l'emplacement du cache de schéma

1. Dans le menu **Outils** , sélectionnez **Options**.

2. Développez **éditeur de texte** , développez **XML** , puis cliquez sur **divers**.

3. Cliquez sur le bouton **Parcourir** dans le champ **schémas** .

4. Sélectionnez le dossier du cache de schéma, puis cliquez sur **OK**.

### <a name="to-add-another-directory-of-common-schemas"></a>Pour ajouter un autre répertoire de schémas courants

1. Modifiez le fichier *catalog.xml* dans le répertoire de cache de schéma de l’éditeur XML.

2. Ajoutez-y un nouvel élément `<Catalog href="..."/>` pointant vers le répertoire contenant les schémas supplémentaires.

3. Enregistrez vos modifications.

   Le catalogue est automatiquement rechargé.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)
