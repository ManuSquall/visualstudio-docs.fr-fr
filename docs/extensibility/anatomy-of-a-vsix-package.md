---
title: "Anatomie d’un Package VSIX | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e728fbe2a9e430224a3da822cbcae45745eeb29e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie d’un Package VSIX
Un package VSIX est un fichier .vsix contenant une ou plusieurs extensions de Visual Studio, ainsi que les métadonnées que Visual Studio utilise pour classifier et installer les extensions. Ces métadonnées sont contenues dans le manifeste VSIX et le fichier [Content_Types] .xml. Un package VSIX peut également contenir un ou plusieurs fichiers Extension.vsixlangpack pour fournir le texte du programme d’installation localisé et peut contenir des packages VSIX supplémentaires pour installer des dépendances.  
  
 Le format de package VSIX suit la norme Open Packaging Conventions (OPC). Le package contient des fichiers binaires et fichiers de prise en charge, ainsi que d’un fichier [Content_Types] .xml et un .vsix fichier manifeste. Un package VSIX peut contenir la sortie de plusieurs projets, ou même plusieurs packages qui ont leurs propres manifestes.  
  
> [!NOTE]
>  Les noms des fichiers inclus dans les packages VSIX ne doivent pas contenir des espaces, ni les caractères réservés dans les identificateurs URI (Uniform Resource), comme définis sous [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Le manifeste VSIX  
 Le manifeste VSIX contient des informations sur l’extension à installer et suit le schéma VSX. Pour plus d’informations, consultez [une Extension de schéma 1.0 référence VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Pour un exemple de manifeste VSIX, consultez [PackageManifest Element (Root Element, VSX Schema)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Le manifeste VSIX doit être nommé `extension.vsixmanifest` lorsqu’il est inclus dans un fichier .vsix.  
  
## <a name="the-content"></a>Le contenu  
 Un package VSIX peut contenir des modèles, des éléments de boîte à outils, des VSPackages ou tout autre type d’extension qui est pris en charge par Visual Studio.  
  
## <a name="language-packs"></a>Modules linguistiques  
 Un package VSIX peut contenir qu’une seule fois ou plusieurs fichiers Extension.vsixlangpack pour fournir du texte localisé pendant l’installation. Pour plus d’informations, consultez [localisation des Packages VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Dépendances et les références  
 Un package VSIX peut contenir d’autres packages VSIX en tant que références. Chacun de ces autres packages doit inclure son propre manifeste VSIX.  
  
 Si un utilisateur tente d’installer une extension qui a des dépendances, le programme d’installation vérifie que les assemblys requis sont installés sur le système de l’utilisateur. Si les assemblys requis sont introuvables, **Extensions et mises à jour** affiche une liste des assemblys manquants.  
  
 Si le manifeste d’extension inclut un ou plusieurs [référence](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) éléments, **Extensions et mises à jour** compare le manifeste de chaque référence pour les extensions qui sont installés sur le système et installe le extension référencée s’il n’est pas déjà installé. Si une version antérieure d’une extension référencée est installée, la nouvelle version remplace.  
  
 Si un projet dans une solution à projets multiples inclut une référence à un autre projet dans la même solution, le package VSIX inclut les dépendances de ce projet. Vous pouvez substituer ce comportement en cliquant sur la référence du projet interne, puis, dans le **propriétés** fenêtre, en définissant le **sortie groupes inclus dans VSIX** propriété `BuiltProjectOutputGroup`.  
  
 Pour inclure les DLL satellites à partir des assemblys référencés dans le package VSIX, ajoutez `SatelliteDllsProjectOutputGroup` à la **sortie groupes inclus dans VSIX** propriété.  
  
## <a name="installation-location"></a>Emplacement d'installation  
 Pendant l’installation, **Extensions et mises à jour** recherche le contenu du package VSIX dans un dossier sous % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Par défaut, l’installation s’applique uniquement à l’utilisateur actuel, car % LocalAppData% est un répertoire spécifique à l’utilisateur. Toutefois, si vous définissez la [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) élément du manifeste pour `True`, l’extension sera installée sous... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions et sera disponible pour tous les utilisateurs de l’ordinateur.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 Le fichier [Content_Types] .xml identifie les types de fichiers dans le fichier .vsix développé. Visual Studio utilise ce fichier lors de l’installation du package, mais n’installe pas le fichier lui-même. Pour plus d’informations sur ce fichier, consultez [la Structure de la [Content_types] .xml fichier](the-structure-of-the-content-types-dot-xml-file.md).  
  
 Un fichier [Content_Types] .xml est requis par l’Open Packaging Conventions (OPC) standard. Pour plus d’informations sur OPC, consultez [OPC : une nouvelle norme pour l’empaquetage de vos données](http://go.microsoft.com/fwlink/?LinkID=148207) sur le site Web MSDN.