---
title: Localisation des forfaits VSIX (en anglais seulement) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702896"
---
# <a name="localizing-vsix-packages"></a>Localisation de packages VSIX

Vous pouvez localiser un package VSIX en créant un fichier *Extension.vsixlangpack* pour chaque langue cible, puis en les plaçant dans le dossier correct. Lorsqu’un paquet localisé est installé, le nom localisé de l’extension est affiché avec une description localisée. Si vous fournissez un fichier de licence localisé, ou une URL qui indique des informations localisées, elles sont également affichées.

Si le contenu de votre forfait VSIX comprend un VSPackage qui ajoute des commandes de menu ou d’autres interfaces utilisateur, consultez [les commandes de menu Localize](../extensibility/localizing-menu-commands.md) pour obtenir de l’information sur la localisation des nouveaux éléments d’interface utilisateur.

## <a name="directory-structure"></a>Structure de répertoires

 Lorsqu’un utilisateur installe une extension, **Extensions and Updates** vérifie le niveau supérieur du forfait VSIX pour un dossier dont le nom correspond au local Visual Studio de l’ordinateur cible. Si **Extensions et Mises à jour** trouve un fichier *.vsixlangpack* dans le dossier, il remplace les valeurs localisées dans ce fichier pour les valeurs correspondantes dans le fichier *.vsixmanifest.* Ces valeurs s’affichent lors de l’installation de l’extension. L’exemple suivant montre la structure d’annuaire d’un package VSIX localisé en espagnol (es-ES) et en Français (fr-FR).

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
> Les modèles de projet soutenus [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] par VSIX dans le générer un manifeste VSIX et le nom *source.extension.vsixmanifest*. Lorsque Visual Studio construit le projet, il copie le contenu de ce fichier dans Extension.VsixManifest dans le paquet VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Le fichier Extension.vsixlangpack

Le fichier *Extension.vsixlangpack* suit le [schéma VSIX Language Pack 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Ce schéma a `PackageLanguagePackManifest`un , qui `Metadata` est immédiatement suivi par un élément enfant. L’élément métadonnée peut contenir jusqu’à 6 `ReleaseNotes`éléments `Icon`pour enfants, `DisplayName`, , `Description` `MoreInfo`, `License`, et . Ces éléments pour `DisplayName`enfants `Description` `MoreInfo`correspondent `License` `ReleaseNotes`aux `Icon` éléments , `Metadata` , , et enfant de l’élément du fichier *Extension.vsixmanifest.*

Lorsque vous créez un fichier vsixlangpack, vous devez définir la `Include in Vsix` propriété à `true`. Dans le cas contraire, le texte d’installation localisé sera ignoré.

### <a name="to-set-the-include-in-vsix-property"></a>Pour définir la propriété Inclure dans la propriété Vsix

1. Dans **Solution Explorer**, cliquez à droite sur le fichier Extension.vsixlangpack, puis cliquez sur **Propriétés**.

2. Dans la **grille de propriété**, cliquez sur Inclure dans **Vsix**, et définir sa valeur à `true`.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre des parties pertinentes d’un fichier *Extension.vsixmanifest.* Le fichier comprend également le fichier *Extension.vsixlangpack* correspondant pour l’espagnol. Les valeurs du pack linguistique remplacent les valeurs du manifeste si le visual Studio local de l’ordinateur cible est réglé sur l’espagnol.

### <a name="code"></a>Code

- [*Extension.vsixmanifest*]

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

- [*Extension.vsixlangpack*]

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
|[VSIX Language Pack schema 2.0 référence](vsix-language-pack-schema-2-0-reference.md)|Un pack linguistique VSIX décrit les informations de localisation d’un fichier de déploiement .vsix.|
|[Anatomie d’un paquet VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Décrit la structure et le contenu d’un paquet vsix.|
|[Localiser les commandes de menu](../extensibility/localizing-menu-commands.md)|Montre comment localiser d’autres ressources textuelles dans une extension.|
