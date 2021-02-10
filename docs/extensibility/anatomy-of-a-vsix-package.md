---
title: Anatomie d’un package VSIX | Microsoft Docs
description: En savoir plus sur le contenu d’un package VSIX dans Visual Studio, un fichier qui contient une ou plusieurs extensions Visual Studio et un fichier manifeste de métadonnées.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d25430206129f0236661222b92cefdbe538a7ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933568"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie d’un package VSIX
Un package VSIX est un fichier *. vsix* qui contient une ou plusieurs extensions Visual Studio, ainsi que les métadonnées utilisées par Visual Studio pour classer et installer les extensions. Ces métadonnées sont contenues dans le manifeste VSIX et le fichier *[Content_Types]. xml* . Un package VSIX peut également contenir un ou plusieurs fichiers *extension. vsixlangpack* pour fournir un texte d’installation localisé et peut contenir des packages VSIX supplémentaires pour installer les dépendances.

 Le format de package VSIX suit la norme OPC (Open Packaging Conventions). Le package contient des fichiers binaires et des fichiers de prise en charge, ainsi qu’un fichier *[Content_Types]. xml* et un fichier manifeste *. vsix* . Un package VSIX peut contenir la sortie de plusieurs projets, voire plusieurs packages ayant leurs propres manifestes.

> [!NOTE]
> Les noms des fichiers inclus dans les packages VSIX ne doivent pas inclure d’espaces, ni de caractères réservés dans les URI (Uniform Resource Identifier), comme défini sous [ \[ rfc2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>Manifeste VSIX
 Le manifeste VSIX contient des informations sur l’extension à installer et suit le schéma VSX. Pour plus d’informations, consultez [Référence du schéma d’extension VSIX 1,0](/previous-versions/dd393700(v=vs.110)). Pour obtenir un exemple de manifeste VSIX, consultez [élément PackageManifest (élément racine, schéma VSX)](/previous-versions/dd393754(v=vs.110)).

 Le manifeste VSIX doit être nommé `extension.vsixmanifest` lorsqu’il est inclus dans un fichier ^. vsix *.

## <a name="the-content"></a>Le contenu
 Un package VSIX peut contenir des modèles, des éléments de boîte à outils, des VSPackages ou tout autre type d’extension pris en charge par Visual Studio.

## <a name="language-packs"></a>Modules linguistiques
 Un package VSIX peut contenir une ou plusieurs fichiers *extension. vsixlangpack* pour fournir du texte localisé au cours de l’installation. Pour plus d’informations, consultez [Localizing VSIX packages](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Dépendances et références
 Un package VSIX peut contenir d’autres packages VSIX en tant que références. Chacun de ces autres packages doit inclure son propre manifeste VSIX.

 Si un utilisateur tente d’installer une extension qui a des dépendances, le programme d’installation vérifie que les assemblys requis sont installés sur le système de l’utilisateur. Si les assemblys requis sont introuvables, les **extensions et les mises à jour** affichent la liste des assemblys manquants.

 Si le manifeste de l’extension contient un ou plusieurs éléments de [référence](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) , les **extensions et les mises à jour** comparent le manifeste de chaque référence aux extensions qui sont installées sur le système et installent l’extension référencée si elle n’est pas déjà installée. Si une version antérieure d’une extension référencée est installée, la version la plus récente la remplace.

 Si un projet dans une solution à plusieurs projets comprend une référence à un autre projet dans la même solution, le package VSIX comprend les dépendances de ce projet. Vous pouvez remplacer ce comportement en sélectionnant la référence du projet interne, puis, dans la fenêtre **Propriétés** , en affectant à la propriété **groupes de sorties inclus dans** la propriété VSIX la valeur `BuiltProjectOutputGroup` .

 Pour inclure des dll satellites à partir d’assemblys référencés dans le package VSIX, ajoutez `SatelliteDllsProjectOutputGroup` aux **groupes de sorties inclus dans** la propriété VSIX.

## <a name="installation-location"></a>Emplacement d'installation
 Pendant l’installation, les **extensions et les mises à jour** recherchent le contenu du package VSIX dans un dossier sous *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.

 Par défaut, l’installation s’applique uniquement à l’utilisateur actuel, car *% LocalAppData%* est un répertoire spécifique à l’utilisateur. Toutefois, si vous affectez à l’élément [ALLUSERS](/previous-versions/ee191547(v=vs.110)) du manifeste la valeur `True` , l’extension sera installée sous <em>. \\ </em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> et sera disponible pour tous les utilisateurs de l’ordinateur.

## <a name="content_typesxml"></a>[Content_Types]. Xml
 Le fichier *[Content_Types]. xml* identifie les types de fichiers dans le fichier *. vsix* développé. Visual Studio utilise ce fichier lors de l’installation du package, mais n’installe pas le fichier lui-même. Pour plus d’informations sur ce fichier, consultez [la structure du fichier [Content_Types]. xml](the-structure-of-the-content-types-dot-xml-file.md).

 Un fichier *[Content_Types]. xml* est requis par la norme OPC (Open Packaging Conventions). Pour plus d’informations sur OPC, consultez [OPC : nouvelle norme pour l’empaquetage de vos données](/archive/blogs/msdnmagazine/opc-a-new-standard-for-packaging-your-data) sur le site Web MSDN.