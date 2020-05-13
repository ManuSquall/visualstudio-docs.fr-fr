---
title: VSIX Extension Schema 2.0 Référence Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78e260c62d67afc10fea25d52169c48b64c82f72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697914"
---
# <a name="vsix-extension-schema-20-reference"></a>SCHÉMA d’extension VSIX 2.0 référence
Un fichier manifeste de déploiement VSIX décrit le contenu d’un package VSIX. Le format de fichier est régi par un schéma. La version 2.0 de ce schéma prend en charge l’ajout de types et d’attributs personnalisés.  Le schéma du manifeste est extensible. Le chargeur manifeste ignore les éléments XML et les attributs qu’il ne comprend pas.

> [!IMPORTANT]
> Visual Studio 2015 peut charger des fichiers VSIX dans les formats Visual Studio 2010, Visual Studio 2012 ou Visual Studio 2013.

## <a name="package-manifest-schema"></a>Schéma manifeste de paquet
 L’élément racine du fichier `<PackageManifest>`manifeste XML est . Il a un `Version`attribut unique , qui est la version du format manifeste. Si des modifications majeures sont apportées au format, le format de la version est modifié. Cet article décrit la version de format manifeste 2.0, `Version` qui est spécifiée dans le manifeste en définissant l’attribut à la valeur de la version 2.0" .

### <a name="packagemanifest-element"></a>Élément PackageManifest
 Dans `<PackageManifest>` l’élément racine, vous pouvez utiliser les éléments suivants :

- `<Metadata>`- Métadonnées et informations publicitaires sur le paquet lui-même. Un `Metadata` seul élément est autorisé dans le manifeste.

- `<Installation>`- Cette section définit la façon dont ce paquet d’extension peut être installé, y compris l’application SKUs qu’il peut installer dans. Un seul `Installation` élément est autorisé dans le manifeste. Un manifeste doit `Installation` avoir un élément, ou ce paquet ne sera pas installé dans n’importe quel SKU.

- `<Dependencies>`- Une liste facultative des dépendances pour ce paquet sont définies ici.

- `<Assets>`- Cette section contient tous les actifs contenus dans ce paquet. Sans cette section, ce paquet ne fera surface aucun contenu.

- `<AnyElement>*`- Le schéma manifeste est suffisamment souple pour permettre à d’autres éléments. Tous les éléments pour enfants non reconnus par le chargeur manifeste sont exposés dans l’API du gestionnaire d’extension comme des objets XmlElement supplémentaires. À l’aide de ces éléments pour enfants, les extensions VSIX peuvent définir des données supplémentaires dans le fichier manifeste auxquelles le code en cours d’exécution dans Visual Studio peut accéder au moment de l’exécution. Voir [Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Élément métadonnée
 Cette section est les métadonnées sur le paquet, son identité et l’information publicitaire. `<Metadata>`contient les éléments suivants :

- `<Identity>`- Définit les informations d’identification de ce paquet et inclut les attributs suivants :

  - `Id`- Cet attribut doit être une pièce d’identité unique pour le paquet choisi par son auteur. Le nom doit être qualifié de la même façon que les types CLR sont namespaced: Company.Product.Feature.Name. L’attribut `Id` est limité à 100 caractères.

  - `Version`- Définit la version de ce paquet et son contenu. Cet attribut suit le format de version d’assemblage CLR : Major.Minor.Build.Revision (1.2.40308.00). Un paquet avec un numéro de version plus élevé est considéré comme des mises à jour du paquet, et peut être installé sur la version installée existante.

  - `Language`- Cet attribut est le langage par défaut pour le paquet et correspond aux données textuelles dans ce manifeste. Cet attribut fait suite à la convention de code local CLR pour les assemblages de ressources, par exemple : en-us, fr-fr. Vous pouvez `neutral` spécifier pour déclarer une extension neutre en langue qui s’exécutera sur n’importe quelle version de Visual Studio. La valeur par défaut est `neutral`.

  - `Publisher`- Cet attribut identifie l’éditeur de ce paquet, soit un nom d’entreprise ou un nom individuel. L’attribut `Publisher` est limité à 100 caractères.

- `<DisplayName>`- Cet élément spécifie le nom du paquet convivial qui est affiché dans l’interface utilisateur de gestionnaire d’extension. Le `DisplayName` contenu est limité à 50 caractères.

- `<Description>`- Cet élément optionnel est une courte description du paquet et de son contenu qui est affiché dans l’interface utilisateur de gestionnaire d’extension. Le `Description` contenu peut contenir n’importe quel texte que vous voulez, mais il est limité à 1000 caractères.

- `<MoreInfo>`- Cet élément optionnel est une URL à une page en ligne qui contient une description complète de ce paquet. Le protocole doit être spécifié comme http.

- `<License>`- Cet élément facultatif est un chemin relatif vers un fichier de licence (.txt, .rtf) contenu dans le paquet.

- `<ReleaseNotes>`- Cet élément facultatif est soit un chemin relatif vers un fichier de notes de sortie contenu dans le paquet (.txt, .rtf) ou bien une URL vers un site Web qui affiche les notes de sortie.

- `<Icon>`- Cet élément optionnel est un chemin relatif vers un fichier d’image (png, bmp, jpeg, ico) contenu dans le paquet. L’image d’icône doit être 32x32 pixels (ou sera réduite à cette taille) et apparaît dans l’interface utilisateur listview. Si `Icon` aucun élément n’est spécifié, l’interface utilisateur utilise un défaut.

- `<PreviewImage>`- Cet élément optionnel est un chemin relatif vers un fichier d’image (png, bmp, jpeg) contenu dans le paquet. L’image de prévisualisation doit être 200x200 pixels, et affichée dans les détails UI. Si `PreviewImage` aucun élément n’est spécifié, l’interface utilisateur utilise un défaut.

- `<Tags>`- Cet élément optionnel répertorie d’autres balises de texte délimitées par des semi-colons qui sont utilisées pour les conseils de recherche. L’élément `Tags` est limité à 100 caractères.

- `<GettingStartedGuide>`- Cet élément optionnel est soit un chemin relatif vers un fichier HTML ou une URL vers un site Web qui contient des informations sur la façon d’utiliser l’extension ou le contenu dans ce paquet. Ce guide est lancé dans le cadre d’une installation.

- `<AnyElement>*`- Le schéma manifeste est suffisamment souple pour permettre à d’autres éléments. Tous les éléments pour enfants qui ne sont pas reconnus par le chargeur manifeste sont exposés comme une liste d’objets XmlElement. À l’aide de ces éléments pour enfants, les extensions VSIX peuvent définir des données supplémentaires dans le fichier manifeste et les énumérer au moment de l’exécution.

### <a name="installation-element"></a>Élément d’installation
 Cette section définit la façon dont ce paquet peut être installé et l’application SKUs qu’il peut installer dans. Cette section contient les attributs suivants :

- `Experimental`- Définissez cet attribut à vrai si vous avez une extension qui est actuellement installée pour tous les utilisateurs, mais vous développez une version mise à jour sur le même ordinateur. Par exemple, si vous avez installé MyExtension 1.0 pour tous les utilisateurs, mais que vous souhaitez déboiffer MyExtension 2.0 sur le même ordinateur, définissez Experimental "vrai". Cet attribut est disponible dans Visual Studio 2015 Update 1 et plus tard.

- `Scope`- Cet attribut peut prendre la valeur "Global" ou "ProductExtension":

  - "Global" précise que l’installation n’est pas étendue à un SKU spécifique. Par exemple, cette valeur est utilisée lors de l’installation d’un SDK Extension.

  - "ProductExtension" précise qu’une extension VSIX traditionnelle (version 1.0) étendue à des SKUs individuels visual Studio est installée. Il s’agit de la valeur par défaut.

- `AllUsers`- Cet attribut optionnel précise si ce paquet sera installé pour tous les utilisateurs. Par défaut, cet attribut est faux, ce qui spécifie que le paquet est par utilisateur. (Lorsque vous définissez cette valeur pour la réalité, l’utilisateur installant doit élever au niveau de privilège administratif pour installer le VSIX qui en résulte.

- `InstalledByMsi`- Cet attribut optionnel précise si ce paquet est installé par un MSI. Les paquets installés par un MSI sont installés et gérés par MSI (Programmes et Fonctionnalités) et non par le Visual Studio Extension Manager.  Par défaut, cet attribut est faux, ce qui spécifie que le paquet n’est pas installé par un MSI.

- `SystemComponent`- Cet attribut facultatif précise si ce paquet doit être considéré comme un composant du système. Les composants du système ne s’affichent pas dans l’interface utilisateur du gestionnaire d’extension et ne peuvent pas être mis à jour. Par défaut, cet attribut est faux, ce qui spécifie que le paquet n’est pas un composant système.

- `AnyAttribute*`- `Installation` L’élément accepte un ensemble ouvert d’attributs qui seront exposés au moment de l’exécution comme un dictionnaire de paires de valeur nominale.

- `<InstallationTarget>`-Cet élément contrôle l’emplacement où l’installateur VSIX installe le paquet. Si la valeur `Scope` de l’attribut est "ProductExtension", le paquet doit cibler un SKU, qui a installé un fichier manifeste dans le cadre de son contenu pour annoncer sa disponibilité aux extensions. L’élément `<InstallationTarget>` a les attributs suivants lorsque l’attribut `Scope` a la valeur explicite ou par défaut "ProductExtension":

  - `Id`- Cet attribut identifie le paquet.  L’attribut suit la convention namespace: Company.Product.Feature.Name. L’attribut `Id` ne peut contenir que des caractères alphanumériques et est limité à 100 caractères. Valeurs attendues :

    - Microsoft.VisualStudio.IntegratedShell Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium (en anglais seulement)

    - Microsoft.VisualStudio.Ultimate (en anglais seulement)

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS (en anglais seulement)

    - My.Shell.App (en)

  - `Version`- Cet attribut spécifie une gamme de versions avec les versions minimales et maximales prises en charge de ce SKU. Un paquet peut détailler les versions des SKU qu’il prend en charge. La notation de la gamme de versions est [10.0 - 11.0], où

    - [ - version minimale inclusive.

    - ] - version maximale inclusive.

    - ( - version minimale exclusive.

    - ) - version maximale exclusive.

    - Version unique - seulement la version spécifiée.

    > [!IMPORTANT]
    > La version 2.0 du SCHEma VSIX a été introduite dans Visual Studio 2012. Pour utiliser ce schéma, vous devez avoir Visual Studio 2012 ou plus tard installé sur la machine et utiliser le VSIXInstaller.exe qui fait partie de ce produit. Vous pouvez cibler les versions antérieures de Visual Studio avec un Visual Studio 2012 ou plus tard VSIXInstaller, mais seulement en utilisant les versions ultérieures de l’installateur.

    Les numéros de version Visual Studio 2017 peuvent être trouvés à [Visual Studio construire des numéros et des dates de sortie](../install/visual-studio-build-numbers-and-release-dates.md).

    Lors de l’expression de la version pour Visual Studio 2017 versions, la version mineure doit toujours être **0**. Par exemple, Visual Studio 2017 version 15.3.26730.0 devrait être exprimée comme [15.0.26730.0,16.0). Ceci n’est nécessaire que pour Visual Studio 2017 et les numéros de version ultérieure.

  - `AnyAttribute*`- `<InstallationTarget>` L’élément permet un ensemble ouvert d’attributs qui est exposé au moment de l’exécution comme un dictionnaire de paire de valeur nominale.

### <a name="dependencies-element"></a>Élément dépendance
 Cet élément contient une liste de dépendances que ce paquet déclare. Si des dépendances sont spécifiées, ces `Id`paquets (identifiés par leur) doivent avoir été installés avant.

- `<Dependency>`élément - Cet élément enfant a les attributs suivants :

  - `Id`- Cet attribut doit être une pièce d’identité unique pour l’emballage dépendant. Cette valeur d’identité doit correspondre à l’attribut `<Metadata><Identity>Id` d’un paquet dont ce paquet dépend. L’attribut `Id` suit la convention namespace: Company.Product.Feature.Name. L’attribut ne peut contenir que des caractères alphanumériques et est limité à 100 caractères.

  - `Version`- Cet attribut spécifie une gamme de versions avec les versions minimales et maximales prises en charge de ce SKU. Un paquet peut détailler les versions des SKU qu’il prend en charge. La notation de gamme de version est [12.0, 13.0], où :

    - [ - version minimale inclusive.

    - ] - version maximale inclusive.

    - ( - version minimale exclusive.

    - ) - version maximale exclusive.

    - Version unique - seulement la version spécifiée.

  - `DisplayName`- Cet attribut est le nom d’affichage du paquet dépendant, qui est utilisé dans les éléments d’interface utilisateur tels que les boîtes de dialogue et les messages d’erreur. L’attribut est facultatif à moins que le paquet à charge ne soit installé par MSI.

  - `Location`- Cet attribut optionnel spécifie soit le chemin relatif dans ce VSIX à un paquet VSIX imbriqué ou une URL à l’emplacement de téléchargement pour la dépendance. Cet attribut est utilisé pour aider l’utilisateur à localiser le paquet préalable.

  - `AnyAttribute*`- `Dependency` L’élément accepte un ensemble ouvert d’attributs qui seront exposés au moment de l’exécution comme un dictionnaire de paires de valeur nominale.

### <a name="assets-element"></a>Élément actif
 Cet élément contient `<Asset>` une liste d’balises pour chaque élément d’extension ou de contenu fait surface par ce paquet.

- `<Asset>`- Cet élément contient les attributs et les éléments suivants :

  - `Type`- Type d’extension ou de contenu représenté par cet élément. Chaque `<Asset>` élément doit `Type`avoir un `<Asset>` seul , `Type`mais plusieurs éléments peuvent avoir le même . Cet attribut doit être représenté comme un nom entièrement qualifié, selon les conventions namespace. Les types connus sont les :

    1. Microsoft.VisualStudio.VsPackage (en anglais seulement)

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl (en anglais seulement)

    4. Microsoft.VisualStudio.Échantillons

    5. Microsoft.VisualStudio.ProjectTemplate (en anglais seulement)

    6. Microsoft.VisualStudio.ItemTemplate (en anglais seulement)

    7. Microsoft.VisualStudio.Assembly (en anglais seulement)

       Vous pouvez créer vos propres types et leur donner des noms uniques. À l’heure de l’exécution à l’intérieur de Visual Studio, votre code peut énumérer et accéder à ces types personnalisés via l’API De gestionnaire d’extension.

  - `Path`- le chemin relatif vers le fichier ou le dossier dans le paquet qui contient l’actif.

  - `TargetVersion`- la plage de version à laquelle l’actif donné s’applique. Utilisé pour l’expédition de plusieurs versions d’actifs à différentes versions de Visual Studio. Nécessite Visual Studio 2017.3 ou plus récent pour avoir un effet.

  - `AnyAttribute*`- Un ensemble ouvert d’attributs qui est exposé au moment de l’exécution comme un dictionnaire de paires de valeur nominale.

    `<AnyElement>*`- Tout contenu structuré `<Asset>` est autorisé entre une balise de départ et de fin. Tous les éléments sont exposés comme une liste d’objets XmlElement. Les extensions VSIX peuvent définir des métadonnées structurées spécifiques au type dans le fichier manifeste et les énumérer au moment de l’exécution.

### <a name="sample-manifest"></a>Exemple manifeste

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

- [Extensions Ship Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
