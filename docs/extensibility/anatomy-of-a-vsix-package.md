---
title: Anatomie d’un forfait VSIX (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6d3f994c531bd36ab4281c5f0b27e993cd3392
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740092"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie d’un paquet VSIX
Un forfait VSIX est un fichier *.vsix* qui contient une ou plusieurs extensions Visual Studio, ainsi que les métadonnées Visual Studio utilise pour classer et installer les extensions. Ces métadonnées sont contenues dans le manifeste VSIX et le fichier *[Content_Types].xml.* Un package VSIX peut également contenir un ou plusieurs fichiers *Extension.vsixlangpack* pour fournir du texte de configuration localisé, et peut contenir des paquets VSIX supplémentaires pour installer des dépendances.

 Le format de forfait VSIX suit la norme Des conventions d’emballage ouvert (CPVP). Le paquet contient des binaires et des fichiers à l’appui, ainsi qu’un fichier *[Content_Types].xml* et un fichier manifeste *.vsix.* Un package VSIX peut contenir la production de plusieurs projets, ou même plusieurs paquets qui ont leurs propres manifestes.

> [!NOTE]
> Les noms des fichiers inclus dans les forfaits VSIX ne doivent pas inclure les espaces, ni les caractères réservés dans Uniform Resource Identifiers (URI), tels que définis dans [ \[RFC2396\]](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>Le manifeste VSIX
 Le manifeste VSIX contient des informations sur l’extension à installer et suit le SCHEma VSX. Pour plus d’informations, voir [vsIX extension schéma 1.0 référence](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Par exemple, VSIX manifeste, voir [l’élément PackageManifest (élément racine, schéma VSX)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

 Le manifeste VSIX `extension.vsixmanifest` doit être nommé lorsqu’il est inclus dans un fichier 'vsix'.

## <a name="the-content"></a>Le contenu
 Un package VSIX peut contenir des modèles, des éléments de boîte à outils, des VSPackages ou tout autre type d’extension qui est pris en charge par Visual Studio.

## <a name="language-packs"></a>Modules linguistiques
 Un package VSIX peut contenir une ou plusieurs fichiers *Extension.vsixlangpack* pour fournir du texte localisé pendant l’installation. Pour plus d’informations, voir [Localizing VSIX packages](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Dépendances et références
 Un package VSIX peut contenir d’autres paquets VSIX comme références. Chacun de ces autres paquets doit inclure son propre manifeste VSIX.

 Si un utilisateur tente d’installer une extension qui a des dépendances, l’installateur vérifie que les assemblages requis sont installés sur le système utilisateur. Si les assemblages requis ne sont pas trouvés, **Extensions et Mises à jour** affiche une liste des assemblages manquants.

 Si le manifeste d’extension comprend un ou plusieurs éléments [de référence,](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) **Extensions et Mises à jour** compare le manifeste de chaque référence aux extensions qui sont installées sur le système, et installe l’extension référencée si elle n’est pas déjà installée. Si une version antérieure d’une extension référencée est installée, la version la plus récente la remplace.

 Si un projet dans une solution multi-projets comprend une référence à un autre projet dans la même solution, le paquet VSIX comprend les dépendances de ce projet. Vous pouvez passer outre à ce comportement en cliquant sur la référence pour le projet interne, `BuiltProjectOutputGroup`puis, dans la fenêtre **propriétés,** en définissant les groupes de sortie inclus dans la propriété **VSIX** à .

 Pour inclure les DLL satellites des assemblages référencés dans l’emballage VSIX, ajoutez `SatelliteDllsProjectOutputGroup` aux groupes de sortie inclus dans la propriété **VSIX.**

## <a name="installation-location"></a>Emplacement d'installation
 Pendant l’installation, **Extensions and Updates** recherche le contenu du paquet VSIX dans un dossier inférieur *à %LocalAppData% -Microsoft-VisualStudio-14.0 'Extensions*.

 Par défaut, l’installation ne s’applique qu’à l’utilisateur actuel, car *% LocalAppData%* est un répertoire spécifique à l’utilisateur. Toutefois, si vous définissez l’élément `True` [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) du manifeste à , l’extension sera installée sous <em>.. \\ </em>VisualStudioInstallationFolder<em>'Common7'IDE’Extensions</em> et sera disponible pour tous les utilisateurs de l’ordinateur.

## <a name="content_typesxml"></a>[Content_Types].xml
 Le fichier *[Content_Types].xml* identifie les types de fichiers dans le fichier *.vsix* élargi. Visual Studio utilise ce fichier lors de l’installation du paquet mais n’installe pas le fichier lui-même. Pour plus d’informations sur ce fichier, voir [La structure du fichier [Content_types].xml](the-structure-of-the-content-types-dot-xml-file.md).

 Un fichier *[Content_Types].xml* est exigé par la norme des Conventions d’emballage ouvert (CPVP). Pour de plus amples renseignements sur le CPVP, consultez [le CPVP : une nouvelle norme pour l’emballage de vos données](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) sur le site Web du MSDN.
