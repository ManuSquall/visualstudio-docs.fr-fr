---
title: Localisation des packages VSIX | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702896"
---
# <a name="localizing-vsix-packages"></a>Localisation de packages VSIX

Vous pouvez localiser un package VSIX en créant un fichier *extension. vsixlangpack* pour chaque langue cible, puis en les plaçant dans le dossier approprié. Lors de l’installation d’un package localisé, le nom localisé de l’extension s’affiche avec une description localisée. Si vous fournissez un fichier de licence localisé, ou une URL qui pointe vers des informations localisées, elles sont également affichées.

Si le contenu de votre package VSIX inclut un VSPackage qui ajoute des commandes de menu ou une autre interface utilisateur, consultez [localiser les commandes de menu](../extensibility/localizing-menu-commands.md) pour plus d’informations sur la localisation des nouveaux éléments d’interface utilisateur.

## <a name="directory-structure"></a>Structure de répertoires

 Lorsqu’un utilisateur installe une extension, les **extensions et les mises à jour** vérifient le niveau supérieur du package VSIX pour un dossier dont le nom correspond aux paramètres régionaux de Visual Studio de l’ordinateur cible. Si les **extensions et les mises à jour** recherchent un fichier *. vsixlangpack* dans le dossier, elles remplacent les valeurs localisées dans ce fichier pour les valeurs correspondantes dans le fichier *. vsixmanifest* . Ces valeurs s’affichent lors de l’installation de l’extension. L’exemple suivant illustre la structure de répertoires d’un package VSIX localisé en espagnol (es-ES) et en français (fr-FR).

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Les modèles de projet pris en charge par VSIX dans [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] génèrent un manifeste VSIX et le nomment *source. extension. vsixmanifest*. Lorsque Visual Studio génère le projet, il copie le contenu de ce fichier dans l’extension. VsixManifest dans le package VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Fichier extension. vsixlangpack

Le fichier *extension. vsixlangpack* suit le [schéma du module linguistique VSIX 2,0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Ce schéma a un `PackageLanguagePackManifest` , qui est immédiatement suivi d’un `Metadata` élément enfant. L’élément de métadonnées peut contenir jusqu’à 6 éléments enfants,,,,, `DisplayName` `Description` `MoreInfo` `License` `ReleaseNotes` et `Icon` . Ces éléments enfants correspondent aux éléments enfants,,,, `DisplayName` `Description` `MoreInfo` `License` `ReleaseNotes` et `Icon` de l' `Metadata` élément du fichier *extension. vsixmanifest* .

Lorsque vous créez un fichier vsixlangpack, vous devez affecter à la propriété la valeur `Include in Vsix` `true` . Dans le cas contraire, le texte d’installation localisé sera ignoré.

### <a name="to-set-the-include-in-vsix-property"></a>Pour définir la propriété Include dans VSIX

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier extension. vsixlangpack, puis cliquez sur **Propriétés**.

2. Dans la **grille des propriétés**, cliquez sur **inclure dans VSIX**et affectez-lui la valeur `true` .

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre des parties pertinentes d’un fichier *extension. vsixmanifest* . Le fichier comprend également le fichier *. vsixlangpack d’extension* correspondant pour l’espagnol. Les valeurs du module linguistique remplacent les valeurs du manifeste si les paramètres régionaux Visual Studio de l’ordinateur cible sont définis sur espagnol.

### <a name="code"></a>Code

- [*Extension. vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Extension. vsixlangpack*]

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

|Titre|Description|
|-----------|-----------------|
|[Informations de référence sur le schéma du module linguistique VSIX 2,0](vsix-language-pack-schema-2-0-reference.md)|Un module linguistique VSIX décrit les informations de localisation d’un fichier de déploiement. vsix.|
|[Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Décrit la structure et le contenu d’un package VSIX.|
|[Localiser les commandes de menu](../extensibility/localizing-menu-commands.md)|Montre comment localiser d’autres ressources de texte dans une extension.|
