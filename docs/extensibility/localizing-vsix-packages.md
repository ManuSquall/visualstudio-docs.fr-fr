---
title: Localisation de Packages VSIX | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49908ba5110cf59d0aa4fff6f91bf356ec72c3c2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065283"
---
# <a name="localizing-vsix-packages"></a>Localisation de packages VSIX

Vous pouvez localiser un package VSIX en créant un *Extension.vsixlangpack* de fichiers pour chaque langue cible et en les plaçant dans le dossier approprié. Lorsqu’un package localisé est installé, le nom localisé de l’extension s’affiche avec une description localisée. Si vous fournissez un fichier de licence localisée ou une URL qui pointe vers les informations localisées, ils sont également affichés.

Si le contenu de votre package VSIX inclut un VSPackage qui ajoute les commandes de menu ou de toute autre interface utilisateur, consultez [localiser les commandes de menu](../extensibility/localizing-menu-commands.md) pour plus d’informations sur la localisation des nouveaux éléments d’interface utilisateur.

## <a name="directory-structure"></a>Structure de répertoires

 Lorsqu’un utilisateur installe une extension, **Extensions et mises à jour** vérifie le niveau supérieur du package VSIX un dossier dont le nom correspond aux paramètres régionaux de Visual Studio de l’ordinateur cible. Si **Extensions et mises à jour** recherche un *.vsixlangpack* fichier dans le dossier, il remplace les valeurs localisées dans ce fichier pour les valeurs correspondantes dans le *.vsixmanifest*fichier. Ces valeurs sont affichées lors de l’extension est en cours d’installation. L’exemple suivant montre la structure de répertoires d’un package VSIX est localisée en espagnol (es-ES) et Français (fr-FR).

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
> Les modèles de projet VSIX pris en charge dans les [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] générer un manifeste VSIX et nommez-le *source.extension.vsixmanifest*. Lorsque Visual Studio génère le projet, il copie le contenu de ce fichier dans Extension.VsixManifest dans le package VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Le fichier Extension.vsixlangpack

Le *Extension.vsixlangpack* fichier suit le [schéma du module linguistique VSIX 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Ce schéma comporte un `PackageLanguagePackManifest`, qui est immédiatement suivi par un `Metadata` élément enfant. L’élément de métadonnées peut contenir jusqu'à 6 éléments enfants, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, et `Icon`. Ces éléments enfants correspondent à la `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, et `Icon` éléments enfants de la `Metadata` élément de la *Extension.vsixmanifest*fichier.

Lorsque vous créez un fichier vsixlangpack, vous devez définir le `Include in Vsix` propriété `true`. Sinon, le texte d’installation localisé sera ignoré.

### <a name="to-set-the-include-in-vsix-property"></a>Pour définir l’inclure dans Vsix propriété

1. Dans **l’Explorateur de solutions**, cliquez sur le fichier Extension.vsixlangpack, puis cliquez sur **propriétés**.

2. Dans le **grille des propriétés**, cliquez sur **inclure dans Vsix**et définissez sa valeur sur `true`.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant affiche les parties pertinentes d’une *Extension.vsixmanifest* fichier. Le fichier inclut également le correspondantes *Extension.vsixlangpack* fichier pour l’espagnol. Les valeurs à partir du pack de langue remplacent les valeurs à partir du manifeste si les paramètres régionaux de Visual Studio de l’ordinateur cible sont configuré en espagnol.

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

|Titre|Description|
|-----------|-----------------|
|[Référence du schéma 2.0 de module linguistique VSIX](/visualstudio/extensibility/vsix-language-pack-schema-2-0-reference)|Un module linguistique VSIX décrit les informations de localisation d’un fichier de déploiement .vsix.|
|[Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Décrit la structure et le contenu d’un package vsix.|
|[Localiser des commandes de menu](../extensibility/localizing-menu-commands.md)|Montre comment localiser les autres ressources de texte dans une extension.|