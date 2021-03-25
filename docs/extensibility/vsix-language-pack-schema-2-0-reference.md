---
title: Référence du schéma du module linguistique VSIX 2,0 | Microsoft Docs
description: Le schéma du module linguistique VSIX fournit des informations d’installation localisées pour les packages VSIX. La version 2,0 prend en charge des éléments de localisation supplémentaires.
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.openlocfilehash: 0e7107cb90a79e8cd1a052cd73706d95a782781d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062276"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Informations de référence sur le schéma du module linguistique VSIX 2,0

Le schéma du module linguistique VSIX fournit des informations d’installation localisées pour les packages VSIX. La version 2,0 de ce schéma prend en charge des éléments de localisation supplémentaires.

## <a name="language-pack-schema"></a>Schéma du module linguistique

L’élément racine du fichier de module linguistique est `<PackageLanguagePackManifest>` , avec l’attribut `Version` , qui est la version du format du module linguistique. Cet article décrit la version 2,0 du format du module linguistique, qui est spécifié dans le manifeste en affectant `Version` à l’attribut la valeur `Version="2.0.0"` . L’élément racine contient exactement un `<Metadata>` élément enfant.

### <a name="packagelanguagepackmanifest-element"></a>Élément PackageLanguagePackManifest

Dans l' `<PackageLanguagePackManifest>` élément, l’élément suivant doit exister :

|Intitulé|Description|
|-----------|-----------------|
|`<Metadata>`| Élément conteneur pour toutes les métadonnées de package localisées

### <a name="metadata-element"></a>Metadata, élément

Dans l' `<Metadata>` élément, vous pouvez avoir les éléments suivants :

|Intitulé|Description|
|-----------|-----------------|
|`<DisplayName>`|Nom localisé de l’extension à installer|
|`<Description>`|Description localisée de l’extension à installer|
|`<License>`| Chemin d’accès à une version localisée de la licence de l’extension|
|`<MoreInfo>`| Lien vers des informations localisées sur l’extension|
|`<ReleaseNotes>`| Un chemin d’accès ou un lien vers une version localisée des notes de publication|
|`<Icon>`| Chemin d’accès à une version localisée de l’icône d’extension|

### <a name="sample-manifest"></a>Exemple de manifeste

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Voir aussi

|Intitulé|Description|
|-----------|-----------------|
|[Localisation de packages VSIX](../extensibility/localizing-vsix-packages.md)|Montre comment fournir la prise en charge de l’installation localisée pour un package VSIX.|
|[Informations de référence sur le schéma d’extension VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)|Un manifeste VSIX décrit le contenu d’un fichier de déploiement *. vsix* . Le fichier de déploiement vous permet d’installer une extension Visual Studio à l’aide de la boîte de dialogue **extensions et mises à jour** .|
|[Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Montre comment utiliser la boîte de dialogue **extensions et mises à jour** pour installer, supprimer, activer et désactiver des extensions.|
