---
title: Anatomie d’un package VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 156b221265b4c3c23b795b09b9a50ccb27a63bcf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295643"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie d’un package VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un package VSIX est un fichier. vsix qui contient une ou plusieurs extensions Visual Studio, ainsi que les métadonnées utilisées par Visual Studio pour classer et installer les extensions. Ces métadonnées sont contenues dans le manifeste VSIX et le fichier [Content_Types]. Xml. Un package VSIX peut également contenir un ou plusieurs fichiers extension. vsixlangpack pour fournir un texte d’installation localisé et peut contenir des packages VSIX supplémentaires pour installer les dépendances.  
  
 Le format de package VSIX suit la norme OPC (Open Packaging Conventions). Le package contient des fichiers binaires et des fichiers de prise en charge, ainsi qu’un fichier [Content_Types]. xml et un fichier manifeste. vsix. Un package VSIX peut contenir la sortie de plusieurs projets, voire plusieurs packages ayant leurs propres manifestes.  
  
> [!NOTE]
> Les noms des fichiers inclus dans les packages VSIX ne doivent pas inclure d’espaces, ni de caractères réservés dans les URI (Uniform Resource Identifier), comme défini sous [\[\]rfc2396 ](https://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Manifeste VSIX  
 Le manifeste VSIX contient des informations sur l’extension à installer et suit le schéma VSX. Pour plus d’informations, consultez [Référence du schéma d’extension VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Pour obtenir un exemple de manifeste VSIX, consultez [élément PackageManifest (élément racine, schéma VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Le manifeste VSIX doit être nommé `extension.vsixmanifest` lorsqu’il est inclus dans un fichier. vsix.  
  
## <a name="the-content"></a>Le contenu  
 Un package VSIX peut contenir des modèles, des éléments de boîte à outils, des VSPackages ou tout autre type d’extension pris en charge par Visual Studio.  
  
## <a name="language-packs"></a>Modules linguistiques  
 Un package VSIX peut contenir une ou plusieurs fichiers extension. vsixlangpack pour fournir du texte localisé au cours de l’installation. Pour plus d’informations, consultez [Localizing VSIX packages](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Dépendances et références  
 Un package VSIX peut contenir d’autres packages VSIX en tant que références. Chacun de ces autres packages doit inclure son propre manifeste VSIX.  
  
 Si un utilisateur tente d’installer une extension qui a des dépendances, le programme d’installation vérifie que les assemblys requis sont installés sur le système de l’utilisateur. Si les assemblys requis sont introuvables, les **extensions et les mises à jour** affichent la liste des assemblys manquants.  
  
 Si le manifeste de l’extension contient un ou plusieurs éléments de [référence](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) , les **extensions et les mises à jour** comparent le manifeste de chaque référence aux extensions qui sont installées sur le système et installent l’extension référencée si elle n’est pas déjà installée. Si une version antérieure d’une extension référencée est installée, la version la plus récente la remplace.  
  
 Si un projet dans une solution à plusieurs projets comprend une référence à un autre projet dans la même solution, le package VSIX comprend les dépendances de ce projet. Vous pouvez remplacer ce comportement en cliquant sur la référence du projet interne, puis, dans la fenêtre **Propriétés** , en affectant à la propriété **groupes de sorties inclus dans** la propriété VSIX la valeur `BuiltProjectOutputGroup`.  
  
 Pour inclure des dll satellites à partir d’assemblys référencés dans le package VSIX, ajoutez `SatelliteDllsProjectOutputGroup` aux **groupes de sorties inclus dans** la propriété VSIX.  
  
## <a name="installation-location"></a>Emplacement d'installation  
 Pendant l’installation, les **extensions et les mises à jour** recherchent le contenu du package VSIX dans un dossier sous%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Par défaut, l’installation s’applique uniquement à l’utilisateur actuel, car% LocalAppData% est un répertoire spécifique à l’utilisateur. Toutefois, si vous définissez l’élément [ALLUSERS](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) du manifeste sur `True`, l’extension sera installée sous.\\*VisualStudioInstallationFolder*\Common7\IDE\Extensions et sera disponible pour tous les utilisateurs de l’ordinateur.  
  
## <a name="content_typesxml"></a>[Content_Types].xml  
 Le fichier [Content_Types]. XML identifie les types de fichiers dans le fichier. vsix développé. Visual Studio utilise ce fichier lors de l’installation du package, mais n’installe pas le fichier lui-même. Pour plus d’informations sur ce fichier, consultez [la structure de l’Content_Types fichier\]. xml](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
 Un fichier [Content_Types]. xml est requis par la norme OPC (Open Packaging Conventions). Pour plus d’informations sur OPC, consultez [OPC : nouvelle norme pour l’empaquetage de vos données](https://go.microsoft.com/fwlink/?LinkID=148207) sur le site Web MSDN.
