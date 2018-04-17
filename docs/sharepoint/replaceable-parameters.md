---
title: Paramètres remplaçables | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 696388ca89102d588bd1a291b6f5689dc08e26a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="replaceable-parameters"></a>Paramètres remplaçables
  Paramètres remplaçables, ou *jetons*, peut être utilisée dans les fichiers de projet pour fournir des valeurs pour les éléments de solution SharePoint dont les valeurs réelles ne sont pas connues au moment du design. Ils sont semblables à la norme [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jetons de modèle. Pour plus d’informations, consultez [les paramètres de modèle](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Format de jeton  
 Les jetons commenceront et se terminent par un signe dollar ($). Les jetons employés sont remplacés par des valeurs réelles lorsqu’un projet est empaqueté dans un fichier de package (.wsp) de solution SharePoint au moment du déploiement. Par exemple, le jeton **$SharePoint.Package.Name$** peut correspondre à la chaîne « Test du SharePoint Package ».  
  
## <a name="token-rules"></a>Règles d’émission de jeton  
 Les règles suivantes s’appliquent aux jetons :  
  
-   Les jetons peuvent être spécifiées n’importe où dans une ligne.  
  
-   Les jetons ne peuvent pas s’étendre sur plusieurs lignes.  
  
-   Le même jeton peut être spécifié plusieurs fois sur la même ligne et dans le même fichier.  
  
-   Jetons différents peuvent être spécifiés sur la même ligne.  
  
 Les jetons qui ne suivent pas ces règles sont ignorés sans fournir un avertissement ou une erreur.  
  
 Le remplacement des jetons par des valeurs de chaîne s’effectue immédiatement après la transformation du manifeste, ce qui permet de modèles de manifeste modifiés par un utilisateur pour utiliser les jetons.  
  
### <a name="token-name-resolution"></a>Résolution de noms de jeton  
 Dans la plupart des cas, un jeton prend une valeur spécifique, quelle que soit l’emplacement. Toutefois, si le jeton est lié à un package ou une fonctionnalité, sa valeur dépend où il est contenu. Par exemple, si une fonctionnalité est dans un Package un, le jeton `$SharePoint.Package.Name$` correspond à la valeur « Package A. » Si la même fonctionnalité figure dans le Package B, `$SharePoint.Package.Name$` correspond à « Package B. »  
  
## <a name="tokens-list"></a>Liste des jetons  
 Le tableau suivant répertorie les jetons disponibles.  
  
|Name|Description|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Le nom du fichier projet contenant, par exemple, « NouvProj.csproj ».|  
|$SharePoint.Project.FileNameWithoutExtension$|Le nom du fichier projet contenant sans l’extension de nom de fichier. Par exemple, « NewProj ».|  
|$SharePoint.Project.AssemblyFullName$|Le nom complet (nom fort) du projet contenant l’assembly de sortie.|  
|$SharePoint.Project.AssemblyFileName$|Le nom du projet contenant l’assembly de sortie.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Le nom du projet conteneur de sortie de l’assembly, sans l’extension de nom de fichier.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Le jeton de clé publique du projet contenant de sortie d’assembly, converti en une chaîne. (16 caractères au « x2 » format hexadécimal.)|  
|$SharePoint.Package.Name$|Le nom du package contenant.|  
|$SharePoint.Package.FileName$|Le nom du fichier de définition du package qui le contient.|  
|$SharePoint.Package.FileNameWithoutExtension$|Nom du fichier de définition du package conteneur (sans extension).|  
|$SharePoint.Package.Id$|ID SharePoint du package contenant. Si une fonctionnalité est utilisée dans plusieurs packages, cette valeur changera.|  
|$SharePoint.Feature.FileName$|Le nom du fichier de définition de la fonctionnalité de conteneur, telles que Feature1.feature.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Le nom du fichier de définition de fonction, sans l’extension de nom de fichier.|  
|$SharePoint.Feature.DeploymentPath$|Le nom du dossier qui contient la fonction dans le package. Ce jeton équivaut à la propriété « Chemin de déploiement » dans le Concepteur de fonctionnalités. Un exemple de valeur « Projet1_Fonctionnalite1 ».|  
|$SharePoint.Feature.Id$|ID SharePoint de la fonctionnalité de conteneur. Ce jeton, comme avec tous les jetons de niveau de fonctionnalité, peut être utilisé uniquement par les fichiers inclus dans un package via une fonctionnalité, pas ajouté directement à un package en dehors d’une fonctionnalité.|  
|$SharePoint.ProjectItem.Name$|Le nom de l’élément de projet (et non son nom de fichier), en tant qu’obtenu à partir de **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. AssemblyQualifiedName$|Nom qualifié d’assembly du type qui correspond le [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] du jeton. Le format de la [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] est en minuscules et correspond au format GUID.ToString (autrement dit, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
|$SharePoint.Type. \<GUID >. FullName$|Le nom complet du type correspondant au GUID dans le jeton. Le format du GUID est en minuscule et correspond au format GUID.ToString (autrement dit, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="adding-extensions-to-the-token-replacement-file-extensions-list"></a>Ajout d’Extensions pour le remplacement des jetons liste d’Extensions de fichier  
 Bien que les jetons peuvent théoriquement être utilisés par n’importe quel fichier qui appartient à un projet SharePoint élément inclus dans le package, par défaut, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] recherche les jetons uniquement dans les fichiers de package, les fichiers manifestes et les fichiers ayant les extensions suivantes :  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Composant WebPart  
  
-   DWP  
  
 Ces extensions sont définies par le `<TokenReplacementFileExtensions>` élément dans le fichier Microsoft.VisualStudio.SharePoint.targets, situé dans le... \\< fichiers programme\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools dossier.  
  
 Vous pouvez, toutefois, ajouter des extensions de fichiers supplémentaires à la liste. Pour ce faire, ajoutez un `<TokenReplacementFileExtensions>` élément à n’importe quel élément PropertyGroup dans le fichier de projet SharePoint qui n’est défini avant le \<importation > du fichier de cibles SharePoint.  
  
> [!NOTE]  
>  Étant donné que le remplacement des jetons se produit après la compilation d’un projet, vous ne devez pas ajouter des extensions de fichier pour les types de fichiers qui sont compilés, tel que .cs, .vb ou .resx. Les jetons sont remplacés uniquement dans les fichiers qui ne sont pas compilées.  
  
 Par exemple, pour ajouter les extensions de nom de fichier « .myextension » et « .yourextension » à la liste des extensions de nom de fichier de remplacement de jeton, vous devez ajouter les éléments suivants dans un fichier .csproj :  
  
```  
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
  
 Vous pouvez également ajouter l’extension directement au fichier .targets. Toutefois, cela modifie la liste des extensions pour tous les projets SharePoint empaquetés sur le système local, pas simplement votre propre. Cela peut être pratique lorsque vous êtes le seul développeur sur le système ou si la plupart de vos projets le requièrent. Toutefois, car il est propre au système, cette approche n’est pas très mobile et par conséquent, il est recommandé que vous ajouter toutes les extensions pour le fichier projet à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  