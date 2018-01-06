---
title: Localisation de Packages VSIX | Documents Microsoft
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6b95047348f549073a05060b81874f65d7781918
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="localizing-vsix-packages"></a>Localisation de Packages VSIX

Vous pouvez localiser un package VSIX en créant un fichier Extension.vsixlangpack pour chaque langue cible et en les plaçant dans le dossier approprié. Lorsqu’un package localisé est installé, le nom localisé de l’extension s’affiche avec une description localisée. Si vous fournissez un fichier de licence localisé, ou une URL qui pointe vers les informations localisées, ils sont également affichés.

Si le contenu de votre package VSIX inclut un VSPackage qui ajoute des commandes de menu ou de toute autre interface utilisateur, consultez [localisation des commandes de Menu](../extensibility/localizing-menu-commands.md) pour plus d’informations sur la localisation les nouveaux éléments d’interface utilisateur.

## <a name="directory-structure"></a>Structure de répertoires

 Lorsqu’un utilisateur installe une extension, **Extensions et mises à jour** vérifie le niveau supérieur du package VSIX un dossier dont le nom correspond aux paramètres régionaux de Visual Studio de l’ordinateur cible. Si **Extensions et mises à jour** trouve une .vsixlangpack file dans le dossier, il remplace les valeurs localisées dans ce fichier pour les valeurs correspondantes dans le fichier .vsixmanifest. Ces valeurs sont affichées lorsque l’extension est en cours d’installation. L’exemple suivant montre la structure de répertoires d’un package VSIX est localisée en espagnol (es-ES) et Français (fr-FR).  

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
> Les modèles de projet de prise en charge de VSIX dans le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] générer un manifeste VSIX et nommez-le source.extension.vsixmanifest. Lorsque Visual Studio génère le projet, il copie le contenu de ce fichier dans Extension.VsixManifest du package VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Le fichier Extension.vsixlangpack

Le fichier Extension.vsixlangpack suit le [le schéma VSIX Language Pack 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Ce schéma comporte un `PackageLanguagePackManifest`, qui est immédiatement suivi par un `Metadata` élément enfant. L’élément de métadonnées peut contenir jusqu'à 6 éléments enfants, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, et `Icon`. Ces éléments enfants correspondent à la `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, et `Icon` des éléments enfants de le `Metadata` élément du fichier Extension.vsixmanifest.

Lorsque vous créez un fichier vsixlangpack, vous devez définir le `Include in Vsix` propriété `true`. Dans le cas contraire, le texte d’installation localisé sera ignoré.

### <a name="to-set-the-include-in-vsix-property"></a>Pour définir l’inclure dans Vsix propriété

1. Dans **l’Explorateur de solutions**, cliquez sur le fichier Extension.vsixlangpack, puis cliquez sur **propriétés**.

2.  Dans la grille des propriétés, cliquez sur **inclure dans Vsix**et définissez sa valeur sur `true`.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre les parties pertinentes d’un fichier Extension.vsixmanifest, ainsi que le fichier Extension.vsixlangpack correspondant pour l’espagnol. Les valeurs du module linguistique remplacent les valeurs à partir du manifeste si les paramètres régionaux de Visual Studio de l’ordinateur cible sont définie pour l’espagnol.

### <a name="code"></a>Code

 [Extension.vsixmanifest]

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

 [Extension.vsixlangpack]

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
|[Référence du schéma de LanguagePack 2.0 VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Un module linguistique VSIX décrit les informations de localisation d’un fichier de déploiement .vsix.|
|[Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Décrit la structure et le contenu d’un package vsix.|
|[Localisation des commandes de menu](../extensibility/localizing-menu-commands.md)|Indique comment localiser les autres ressources de texte dans une extension.|