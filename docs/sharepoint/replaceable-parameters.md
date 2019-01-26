---
title: Paramètres remplaçables | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload: office
ms.openlocfilehash: 792c7faf9ed704dd01226c750e9898965111c414
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871947"
---
# <a name="replaceable-parameters"></a>Paramètres remplaçables
  Paramètres remplaçables, ou *jetons*, peut être utilisé à l’intérieur des fichiers projet pour fournir des valeurs pour les éléments de solution SharePoint dont les valeurs réelles ne sont pas connues au moment du design. Ils sont similaires à celui de la norme [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jetons de modèle. Pour plus d’informations, consultez [paramètres de modèle](../ide/template-parameters.md).  
  
## <a name="token-format"></a>Format de jeton
 Les jetons commenceront et se terminent par un caractère de signe dollar ($). Sur le déploiement, les jetons employés sont remplacés par les valeurs réelles lorsqu’un projet est empaqueté dans un package de solution SharePoint (*.wsp* fichier). Par exemple, le jeton **$SharePoint.Package.Name$** susceptibles de résoudre vers la chaîne « Test du Package SharePoint ».  
  
## <a name="token-rules"></a>Règles de jeton
 Les règles suivantes s’appliquent aux jetons :  
  
- Les jetons peuvent être spécifiées n’importe où dans une ligne.  
  
- Les jetons ne peuvent pas couvrir plusieurs lignes.  
  
- Le même jeton peut être spécifié plusieurs fois sur la même ligne et dans le même fichier.  
  
- Jetons différents peuvent être spécifiés sur la même ligne.  
  
  Les jetons qui ne suivent pas ces règles sont ignorées et n’entraînent pas un avertissement ou une erreur.  
  
  Le remplacement des jetons par des valeurs de chaîne est effectué immédiatement après la transformation du manifeste. Ce remplacement permet à l’utilisateur de modifier les modèles de manifeste avec des jetons.  
  
### <a name="token-name-resolution"></a>Résolution de noms de jeton
 Dans la plupart des cas, un jeton est résolu en une valeur spécifique, quel que soit l’endroit où elle est contenue. Toutefois, si le jeton est lié à un package ou une fonctionnalité, sa valeur dépend dans lequel il est contenu. Par exemple, si une fonctionnalité est dans un Package un, le jeton `$SharePoint.Package.Name$` correspond à la valeur « Package A. » Si la même fonctionnalité figure dans le Package B, `$SharePoint.Package.Name$` correspond à « Package b ».  
  
## <a name="tokens-list"></a>Liste des jetons
 Le tableau suivant répertorie les jetons disponibles.  
  
|Name|Description|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Le nom du conteneur de projet fichier, tel que *NouvProj.csproj*.|  
|$SharePoint.Project.FileNameWithoutExtension$|Le nom du fichier projet contenant sans l’extension de nom de fichier. Par exemple, « NewProj ».|  
|$SharePoint.Project.AssemblyFullName$|Le nom complet (nom fort) du projet contenant l’assembly de sortie.|  
|$SharePoint.Project.AssemblyFileName$|Le nom du projet contenant l’assembly de sortie.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Le nom du projet conteneur de sortie d’assembly, sans l’extension de nom de fichier.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Le jeton de clé publique du projet contenant de sortie d’assembly, converti en une chaîne. (16 caractères au « x2 » format hexadécimal.)|  
|$SharePoint.Package.Name$|Le nom du package qui le contient.|  
|$SharePoint.Package.FileName$|Le nom de fichier de définition du package qui le contient.|  
|$SharePoint.Package.FileNameWithoutExtension$|Le nom (sans extension) du fichier de définition du package qui le contient.|  
|$SharePoint.Package.Id$|L’ID de SharePoint pour le package qui le contient. Si une fonctionnalité est utilisée dans plusieurs packages, cette valeur se modifie.|  
|$SharePoint.Feature.FileName$|Le nom du fichier de définition du contenant des fonctionnalités, telles que *Feature1.feature*.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Le nom du fichier de définition de fonction, sans l’extension de nom de fichier.|  
|$SharePoint.Feature.DeploymentPath$|Le nom du dossier qui contient la fonctionnalité dans le package. Ce jeton équivaut à la propriété « Chemin de déploiement » dans le Concepteur de fonctionnalités. Un exemple de valeur « Projet1_Fonctionnalite1 ».|  
|$SharePoint.Feature.Id$|L’ID SharePoint de la fonctionnalité de conteneur. Ce jeton, comme avec tous les jetons de niveau de fonctionnalité, peut être utilisée uniquement par les fichiers inclus dans un package via une fonctionnalité, pas ajouté directement à un package en dehors d’une fonctionnalité.|  
|$SharePoint.ProjectItem.Name$|Le nom de l’élément de projet (et non son nom de fichier), comme obtenu à partir de **ISharePointProjectItem.Name**.|  
|$SharePoint.Type.\<GUID>.AssemblyQualifiedName$|Le nom qualifié assembly du type qui correspond le [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] du jeton. Le format de la [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] est en minuscules et correspond au format GUID.ToString (autrement dit, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
|$SharePoint.Type.\<GUID>.FullName$|Le nom complet du type correspondant au GUID dans le jeton. Le format du GUID est en minuscule et correspond au format GUID.ToString (autrement dit, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Ajouter des extensions à la liste d’extensions de fichier remplacement des jetons
 Bien que les jetons peuvent théoriquement être utilisés par n’importe quel fichier qui appartient à un projet SharePoint élément inclus dans le package, par défaut, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] recherche les jetons uniquement dans les fichiers de package, les fichiers manifestes et les fichiers ayant les extensions suivantes :  
  
- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
- ASCX  
  
- ASPX  
  
- Composant WebPart  
  
- DWP  
  
  Ces extensions sont définies par le `<TokenReplacementFileExtensions>` élément dans le fichier Microsoft.VisualStudio.SharePoint.targets, situé dans le... \\< fichiers programme\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools dossier.  
  
  Vous pouvez, toutefois, ajouter des extensions de fichiers supplémentaires à la liste. Ajouter un `<TokenReplacementFileExtensions>` élément à n’importe quel élément PropertyGroup dans le fichier de projet SharePoint qui est défini avant le \<importation > du fichier de cibles SharePoint.  
  
> [!NOTE]  
>  Étant donné que le remplacement des jetons se produit après la compilation d’un projet, n’ajoutez pas les extensions de fichier pour les types de fichiers qui sont compilés, tels que *.cs*, *.vb* ou *.resx*. Les jetons sont remplacés uniquement dans les fichiers qui ne sont pas compilées.  
  
 Par exemple, pour ajouter les extensions de nom de fichier (*.myextension* et *.yourextension*) à la liste des extensions de nom de fichier de remplacement des jetons, vous devez ajouter le code suivant à un projet (*.csproj* ) fichier :  
  
```xml  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Vous pouvez ajouter l’extension directement vers les cibles (*.targets*) fichier. Toutefois, ajoutez l’extension modifie la liste des extensions pour tous les projets SharePoint empaquetés sur le système local, non seulement vos propres. Cette extension peut être pratique lorsque vous êtes le seul développeur sur le système ou si la plupart de vos projets en avez besoin. Cependant, car il est spécifique au système, cette approche n’est pas portable, et par conséquent, il est recommandé que vous ajoutez toutes les extensions au fichier projet à la place.  
  
## <a name="see-also"></a>Voir aussi
 [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
