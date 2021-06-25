---
title: Informations de référence sur le schéma d’extension VSIX 2,0 | Microsoft Docs
description: Le schéma d’extension VSIX 2,0 définit le format de fichier d’un fichier manifeste de déploiement VSIX, qui décrit le contenu d’un package VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 66393bbe6383fcc6cae942a3d7e86f1d701a9634
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905239"
---
# <a name="vsix-extension-schema-20-reference"></a>Informations de référence sur le schéma d’extension VSIX 2,0
Un fichier manifeste de déploiement VSIX décrit le contenu d’un package VSIX. Le format de fichier est régi par un schéma. La version 2,0 de ce schéma prend en charge l’ajout de types et d’attributs personnalisés.  Le schéma du manifeste est extensible. Le chargeur de manifeste ignore les éléments et les attributs XML qu’il ne comprend pas.

> [!IMPORTANT]
> Visual Studio 2015 peut charger des fichiers VSIX dans les formats Visual Studio 2010, Visual Studio 2012 ou Visual Studio 2013.

## <a name="package-manifest-schema"></a>Schéma de manifeste du package
 L’élément racine du fichier XML manifeste est `<PackageManifest>` . Il a un seul attribut `Version` , qui est la version du format du manifeste. Si des modifications majeures sont apportées au format, le format de version est modifié. Cet article décrit le format du manifeste version 2,0, qui est spécifié dans le manifeste en affectant `Version` à l’attribut la valeur de version = "2.0".

### <a name="packagemanifest-element"></a>Élément PackageManifest
 Dans l' `<PackageManifest>` élément racine, vous pouvez utiliser les éléments suivants :

- `<Metadata>` -Métadonnées et informations de publicité sur le package lui-même. Un seul `Metadata` élément est autorisé dans le manifeste.

- `<Installation>` -Cette section définit la façon dont ce package d’extension peut être installé, y compris les références SKU d’application dans lesquelles il peut être installé. Un seul `Installation` élément est autorisé dans le manifeste. Un manifeste doit avoir un `Installation` élément, ou ce package n’est pas installé dans une référence (SKU).

- `<Dependencies>` -Une liste facultative de dépendances pour ce package est définie ici.

- `<Assets>` -Cette section contient toutes les ressources contenues dans ce package. Sans cette section, ce package n’affichera aucun contenu.

- `<AnyElement>*` -Le schéma de manifeste est suffisamment flexible pour permettre d’autres éléments. Les éléments enfants non reconnus par le chargeur de manifeste sont exposés dans l’API du gestionnaire d’extensions en tant qu’objets XmlElement supplémentaires. À l’aide de ces éléments enfants, les extensions VSIX peuvent définir des données supplémentaires dans le fichier manifeste que le code s’exécutant dans Visual Studio peut accéder au moment de l’exécution. Consultez [Microsoft. VisualStudio. ExtensionManager. IExtension. AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Metadata, élément
 Cette section correspond aux métadonnées relatives au package, à son identité et à la publicité. `<Metadata>` contient les éléments suivants :

- `<Identity>` -Définit les informations d’identification pour ce package et comprend les attributs suivants :

  - `Id` -Cet attribut doit être un ID unique pour le package choisi par son auteur. Le nom doit être qualifié de la même façon que les types CLR sont des espaces de noms : Company.Product.Feature.Name. L' `Id` attribut est limité à 100 caractères.

  - `Version` -Définit la version de ce package et son contenu. Cet attribut suit le format de version de l’assembly CLR : Major. minor. Build. Revision (1.2.40308.00). Un package avec un numéro de version plus élevé est considéré comme des mises à jour du package et peut être installé sur la version installée existante.

  - `Language` -Cet attribut est la langue par défaut pour le package et correspond aux données textuelles de ce manifeste. Cet attribut suit la Convention du code de paramètres régionaux CLR pour les assemblys de ressources, par exemple : en-US, en, fr-fr. Vous pouvez spécifier `neutral` pour déclarer une extension indépendante du langage qui s’exécutera sur n’importe quelle version de Visual Studio. La valeur par défaut est `neutral`.

  - `Publisher` -Cet attribut identifie l’éditeur de ce package, qu’il s’agisse d’une société ou d’un nom individuel. L' `Publisher` attribut est limité à 100 caractères.

- `<DisplayName>` : Cet élément spécifie le nom du package convivial qui s’affiche dans l’interface utilisateur du gestionnaire d’extensions. Le `DisplayName` contenu est limité à 50 caractères.

- `<Description>` -Cet élément facultatif est une brève description du package et de son contenu qui s’affiche dans l’interface utilisateur du gestionnaire d’extensions. Le `Description` contenu peut contenir n’importe quel texte de votre choix, mais il est limité à 1000 caractères.

- `<MoreInfo>` -Cet élément facultatif est une URL vers une page en ligne qui contient une description complète de ce package. Le protocole doit être spécifié en tant que http.

- `<License>` -Cet élément facultatif est un chemin d’accès relatif à un fichier de licence (.txt,. rtf) contenu dans le package.

- `<ReleaseNotes>` -Cet élément facultatif est soit un chemin d’accès relatif à un fichier de notes de publication contenu dans le package (.txt,. rtf), soit une URL vers un site Web qui affiche les notes de publication.

- `<Icon>` -Cet élément facultatif est un chemin d’accès relatif à un fichier image (png, BMP, JPEG, ICO) contenu dans le package. L’image de l’icône doit être de 32x32 pixels (ou sera réduite à cette taille) et apparaîtra dans l’interface utilisateur de ListView. Si aucun `Icon` élément n’est spécifié, l’interface utilisateur utilise une valeur par défaut.

- `<PreviewImage>` -Cet élément facultatif est un chemin d’accès relatif à un fichier image (png, BMP, JPEG) contenu dans le package. L’image d’aperçu doit être 200x200 pixels et s’afficher dans l’interface utilisateur des détails. Si aucun `PreviewImage` élément n’est spécifié, l’interface utilisateur utilise une valeur par défaut.

- `<Tags>` -Cet élément facultatif répertorie les balises de texte supplémentaires délimitées par des points-virgules utilisées pour les indicateurs de recherche. L' `Tags` élément est limité à 100 caractères.

- `<GettingStartedGuide>` -Cet élément facultatif est soit un chemin d’accès relatif à un fichier HTML, soit une URL vers un site Web qui contient des informations sur l’utilisation de l’extension ou du contenu dans ce package. Ce guide est lancé dans le cadre d’une installation de.

- `<AnyElement>*` -Le schéma de manifeste est suffisamment flexible pour permettre d’autres éléments. Les éléments enfants qui ne sont pas reconnus par le chargeur de manifeste sont exposés sous la forme d’une liste d’objets XmlElement. À l’aide de ces éléments enfants, les extensions VSIX peuvent définir des données supplémentaires dans le fichier manifeste et les énumérer au moment de l’exécution.

### <a name="installation-element"></a>Élément d’installation
 Cette section définit la façon dont ce package peut être installé et les références SKU de l’application dans laquelle il peut être installé. Cette section contient les attributs suivants :

- `Experimental` -Affectez la valeur true à cet attribut si une extension est actuellement installée pour tous les utilisateurs, mais que vous développez une version mise à jour sur le même ordinateur. Par exemple, si vous avez installé MyExtension 1,0 pour tous les utilisateurs, mais que vous souhaitez déboguer MyExtension 2,0 sur le même ordinateur, définissez expérimentale = "true". Cet attribut est disponible dans Visual Studio 2015 Update 1 et versions ultérieures.

- `Scope` -Cet attribut peut prendre la valeur « global » ou « ProductExtension » :

  - « Global » indique que l’installation n’est pas limitée à une référence SKU spécifique. Par exemple, cette valeur est utilisée lors de l’installation d’un kit de développement logiciel (SDK) d’extension.

  - « ProductExtension » spécifie qu’une extension VSIX traditionnelle (version 1,0) étendue à des références SKU Visual Studio individuelles est installée. Il s’agit de la valeur par défaut.

- `AllUsers` -Cet attribut facultatif spécifie si ce package doit être installé pour tous les utilisateurs. Par défaut, cet attribut est défini sur false, ce qui spécifie que le package est par utilisateur. (Lorsque vous définissez cette valeur sur true, l’utilisateur d’installation doit élever au niveau de privilège d’administration pour installer le VSIX résultant.

- `InstalledByMsi` -Cet attribut facultatif spécifie si ce package est installé par un MSI. Les packages installés par un MSI sont installés et gérés par MSI (programmes et fonctionnalités) et non par le gestionnaire d’extensions Visual Studio.  Par défaut, cet attribut est défini sur false, ce qui indique que le package n’est pas installé par un MSI.

- `SystemComponent` -Cet attribut facultatif spécifie si ce package doit être considéré comme un composant système. Les composants système ne s’affichent pas dans l’interface utilisateur du gestionnaire d’extensions et ne peuvent pas être mis à jour. Par défaut, cet attribut a la valeur false, ce qui indique que le package n’est pas un composant système.

- `AnyAttribute*` -L' `Installation` élément accepte un ensemble d’attributs Open-fini qui seront exposés au moment de l’exécution en tant que dictionnaire de paires nom-valeur.

- `<InstallationTarget>` : Cet élément contrôle l’emplacement où le programme d’installation VSIX installe le package. Si la valeur de l' `Scope` attribut est « ProductExtension », le package doit cibler une référence (SKU), qui a installé un fichier manifeste dans le cadre de son contenu pour annoncer sa disponibilité aux extensions. L' `<InstallationTarget>` élément a les attributs suivants lorsque l' `Scope` attribut a la valeur explicite ou par défaut « ProductExtension » :

  - `Id` -Cet attribut identifie le package.  L’attribut suit la Convention d’espace de noms : Company.Product.Feature.Name. L' `Id` attribut ne peut contenir que des caractères alphanumériques et est limité à 100 caractères. Valeurs attendues :

    - Microsoft. VisualStudio. IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft. VisualStudio. Premium

    - Microsoft. VisualStudio. Ultimate

    - Microsoft. VisualStudio. VWDExpress

    - Microsoft. VisualStudio. VPDExpress

    - Microsoft. VisualStudio. VSWinExpress

    - Microsoft. VisualStudio. VSLS

    - My.Shell.App

  - `Version` -Cet attribut spécifie une plage de versions avec les versions minimales et maximales prises en charge de cette référence SKU. Un package peut détailler les versions des références SKU qu’il prend en charge. La notation de plage de versions est [10,0-11,0], où

    - [-version inclusive minimale.

    - ]-version inclusive maximale.

    - (-version minimale exclusive.

    - )-version exclusive maximale.

    - Single Version #-seule la version spécifiée.

    > [!IMPORTANT]
    > La version 2,0 du schéma VSIX a été introduite dans Visual Studio 2012. Pour utiliser ce schéma, vous devez avoir installé Visual Studio 2012 ou une version ultérieure sur l’ordinateur et utiliser le VSIXInstaller.exe qui fait partie de ce produit. Vous pouvez cibler des versions antérieures de Visual Studio avec un VSIXInstaller Visual Studio 2012 ou version ultérieure, mais uniquement à l’aide des versions ultérieures du programme d’installation.

    Les numéros de version de Visual Studio 2017 se trouvent dans [les numéros de build et les dates de publication de Visual Studio](../install/visual-studio-build-numbers-and-release-dates.md).

    Lors de l’expression de la version pour les versions de Visual Studio 2017, la version mineure doit toujours être **0**. Par exemple, la version 15.3.26730.0 de Visual Studio 2017 doit être exprimée sous la forme [15.0.26730.0, 16.]. Cela est requis uniquement pour les numéros de version de Visual Studio 2017 et versions ultérieures.

  - `AnyAttribute*` -L' `<InstallationTarget>` élément autorise un ensemble d’attributs Open-fini qui est exposé au moment de l’exécution en tant que dictionnaire de paires nom-valeur.

### <a name="dependencies-element"></a>Élément Dependencies
 Cet élément contient la liste des dépendances déclarées par ce package. Si des dépendances sont spécifiées, ces packages (identifiés par leur `Id` ) doivent avoir été installés avant.

- `<Dependency>` Element : cet élément enfant a les attributs suivants :

  - `Id` -Cet attribut doit être un ID unique pour le package dépendant. Cette valeur d’identité doit correspondre à l' `<Metadata><Identity>Id` attribut d’un package dont ce package dépend. L' `Id` attribut suit la Convention d’espace de noms : Company.Product.Feature.Name. L’attribut ne peut contenir que des caractères alphanumériques et est limité à 100 caractères.

  - `Version` -Cet attribut spécifie une plage de versions avec les versions minimales et maximales prises en charge de cette référence SKU. Un package peut détailler les versions des références SKU qu’il prend en charge. La notation de plage de versions est [12,0, 13,0], où :

    - [-version inclusive minimale.

    - ]-version inclusive maximale.

    - (-version minimale exclusive.

    - )-version exclusive maximale.

    - Single Version #-seule la version spécifiée.

  - `DisplayName` -Cet attribut est le nom complet du package dépendant, qui est utilisé dans les éléments d’interface utilisateur tels que les boîtes de dialogue et les messages d’erreur. L’attribut est facultatif, à moins que le package dépendant ne soit installé par MSI.

  - `Location` -Cet attribut facultatif spécifie le chemin d’accès relatif dans ce VSIX à un package VSIX imbriqué ou une URL vers l’emplacement de téléchargement pour la dépendance. Cet attribut est utilisé pour aider l’utilisateur à localiser le package requis.

  - `AnyAttribute*` -L' `Dependency` élément accepte un ensemble d’attributs Open-fini qui seront exposés au moment de l’exécution en tant que dictionnaire de paires nom-valeur.

### <a name="assets-element"></a>Élément Assets
 Cet élément contient une liste de `<Asset>` balises pour chaque extension ou élément de contenu qui est exposée par ce package.

- `<Asset>` -Cet élément contient les attributs et les éléments suivants :

  - `Type` : Type d’extension ou de contenu représenté par cet élément. Chaque `<Asset>` élément doit avoir un seul `Type` , mais plusieurs `<Asset>` éléments peuvent avoir le même `Type` . Cet attribut doit être représenté sous la forme d’un nom qualifié complet, conformément aux conventions de l’espace de noms. Les types connus sont les suivants :

    1. Microsoft. VisualStudio. VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft. VisualStudio. ToolboxControl

    4. Microsoft. VisualStudio. Samples

    5. Microsoft. VisualStudio. ProjectTemplate

    6. Microsoft. VisualStudio. ItemTemplate

    7. Microsoft. VisualStudio. assembly

       Vous pouvez créer vos propres types et leur attribuer des noms uniques. Au moment de l’exécution dans Visual Studio, votre code peut énumérer et accéder à ces types personnalisés via l’API du gestionnaire d’extensions.

  - `Path` : chemin d’accès relatif au fichier ou dossier dans le package qui contient l’élément multimédia.

  - `TargetVersion` -plage de versions à laquelle s’applique la ressource donnée. Utilisé pour l’expédition de plusieurs versions de ressources vers différentes versions de Visual Studio. Nécessite l’effet de Visual Studio 2017,3 ou une version plus récente.

  - `AnyAttribute*` -Jeu d’attributs Open-fini qui est exposé au moment de l’exécution en tant que dictionnaire de paires nom-valeur.

    `<AnyElement>*` -Tout contenu structuré est autorisé entre une `<Asset>` balise de début et de fin. Tous les éléments sont exposés sous la forme d’une liste d’objets XmlElement. Les extensions VSIX peuvent définir des métadonnées spécifiques au type structuré dans le fichier manifeste et les énumérer au moment de l’exécution.

### <a name="sample-manifest"></a>Exemple de manifeste

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
  <Metadata>
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />
    <DisplayName>Test Package</DisplayName>
    <Description>Information about my package</Description>
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>
    <License>eula.rtf</License>
    <ReleaseNotes>notes.txt</ReleaseNotes>
    <Icon>Images\icon.png</Icon>
    <PreviewImage>Images\preview.png</PreviewImage>
  </Metadata>
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Voir aussi

- [Envoyer des extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
