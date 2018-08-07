---
title: Référence de schéma 2.0 du module linguistique VSIX | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: douge
ms.workload:
- dagriffe
ms.openlocfilehash: e4a8bc0f4b276ed649cdff986bdfc56cf8c77e06
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586220"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Référence de schéma 2.0 du module linguistique VSIX

Le schéma du module linguistique VSIX fournit des informations d’installation localisée des packages VSIX. La version 2.0 de ce schéma prend en charge les éléments de localisation supplémentaires.

## <a name="language-pack-schema"></a>Schéma du module linguistique

L’élément racine du fichier de pack de langue est `<PackageLanguagePackManifest>`, avec un attribut `Version`, qui est la version du format de pack de langue. Cet article décrit la version 2.0 du format de pack de langue, qui est spécifiée dans le manifeste en définissant le `Version` à la valeur d’attribut `Version="2.0.0"`. L’élément racine contient exactement un seul enfant `<Metadata>` élément.

### <a name="packagelangaugepackmanifest-element"></a>Élément de PackageLangaugePackManifest

Dans le `<PackageLanguagePackManifest>` élément l’élément suivant doit exister :
|Titre|Description|
|-----------|-----------------|
|`<Metadata>`| L’élément conteneur pour toutes les métadonnées de la version localisée du package

### <a name="metadata-element"></a>Élément de métadonnées

Dans le `<Metadata>` élément que vous pouvez avoir les éléments suivants :
|Titre|Description|
|-----------|-----------------|
|`<DisplayName>`|Le nom localisé de l’extension à installer|
|`<Description>`|La description localisée de l’extension à installer|
|`<License>`| Un chemin d’accès à une version localisée de la licence de l’extension|
|`<MoreInfo>`| Un lien vers des informations localisées sur l’extension|
|`<ReleaseNotes>`| Un chemin d’accès ou un lien vers une version localisée des notes de publication|
|`<Icon>`| Un chemin d’accès à une version localisée de l’icône des extensions|

### <a name="sample-manifest"></a>Exemple de fichier manifeste

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Voir aussi

|Titre|Description|
|-----------|-----------------|
|[Localisation de packages VSIX](../extensibility/localizing-vsix-packages.md)|Montre comment fournir un support d’installation localisé pour un package VSIX.|
|[Référence de schéma 2.0 d’extension VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)|Un manifeste VSIX décrit le contenu d’un *.vsix* fichier de déploiement. Le fichier de déploiement vous permet d’installer une extension Visual Studio à l’aide de la **Extensions et mises à jour** boîte de dialogue.|
|[Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Montre comment utiliser le **Extensions et mises à jour** boîte de dialogue pour installer, supprimer, activer et désactiver des extensions.|