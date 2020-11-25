---
title: Paramètres remplaçables | Microsoft Docs
description: Passez en revue les paramètres remplaçables (jetons), qui spécifient des valeurs dans les fichiers projet pour les éléments de solution SharePoint dont les valeurs réelles ne sont pas connues au moment de la conception.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1cd44b3edfaeae376e5a4a9698d138bd75c03bf8
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970256"
---
# <a name="replaceable-parameters"></a>Paramètres remplaçables
  Les paramètres remplaçables, ou *jetons*, peuvent être utilisés dans les fichiers projet pour fournir des valeurs pour les éléments de solution SharePoint dont les valeurs réelles ne sont pas connues au moment de la conception. Elles sont similaires en fonction des jetons de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modèle standard. Pour plus d’informations, consultez [paramètres de modèle](../ide/template-parameters.md).

## <a name="token-format"></a>Format de jeton
 Les jetons commencent et se terminent par un caractère dollar ($). Lors du déploiement, tous les jetons utilisés sont remplacés par les valeurs réelles lorsqu’un projet est empaqueté dans un package de solution SharePoint (fichier *. wsp* ). Par exemple, le jeton **$SharePoint. Package.Name $** peut être résolu en chaîne « test package SharePoint ».

## <a name="token-rules"></a>Règles de jeton
 Les règles suivantes s’appliquent aux jetons :

- Les jetons peuvent être spécifiés n’importe où sur une ligne.

- Les jetons ne peuvent pas s’étendre sur plusieurs lignes.

- Le même jeton peut être spécifié plusieurs fois sur la même ligne et dans le même fichier.

- Différents jetons peuvent être spécifiés sur la même ligne.

  Les jetons qui ne respectent pas ces règles sont ignorés et ne génèrent pas d’avertissement ni d’erreur.

  Le remplacement des jetons par les valeurs de chaîne est effectué immédiatement après la transformation du manifeste. Ce remplacement permet à l’utilisateur de modifier les modèles de manifeste avec des jetons.

### <a name="token-name-resolution"></a>Résolution de noms de jeton
 Dans la plupart des cas, un jeton correspond à une valeur spécifique, quel que soit l’emplacement où il est contenu. Toutefois, si le jeton est lié à un package ou une fonctionnalité, la valeur du jeton dépend de son emplacement. Par exemple, si une fonctionnalité se trouve dans le package A, le jeton est `$SharePoint.Package.Name$` résolu en la valeur « package a ». Si la même fonctionnalité se trouve dans le package B, elle est `$SharePoint.Package.Name$` résolue en « package b ».

## <a name="tokens-list"></a>Liste des jetons
 Le tableau suivant répertorie les jetons disponibles.

|Nom|Description|
|----------|-----------------|
|$SharePoint. Project. FileName $|Nom du fichier projet contenant, par exemple, *NewProj. csproj*.|
|$SharePoint. Project. FileNameWithoutExtension $|Nom du fichier projet conteneur sans l’extension de nom de fichier. Par exemple, « NewProj ».|
|$SharePoint. Project. AssemblyFullName $|Nom complet (nom fort) de l’assembly de sortie du projet conteneur.|
|$SharePoint. Project. AssemblyFileName $|Nom de l’assembly de sortie du projet conteneur.|
|$SharePoint. Project. AssemblyFileNameWithoutExtension $|Nom de l’assembly de sortie du projet conteneur, sans l’extension de nom de fichier.|
|$SharePoint. Project. AssemblyPublicKeyToken $|Jeton de clé publique de l’assembly de sortie du projet conteneur, converti en chaîne. (16 caractères au format hexadécimal « x2 ».)|
|$SharePoint. Package.Name $|Nom du package conteneur.|
|$SharePoint. Package. FileName $|Nom du fichier de définition du package conteneur.|
|$SharePoint. Package. FileNameWithoutExtension $|Nom (sans extension) du fichier de définition du package conteneur.|
|$SharePoint. Package.Id $|ID SharePoint pour le package contenant. Si une fonctionnalité est utilisée dans plusieurs packages, cette valeur sera modifiée.|
|$SharePoint. Feature. FileName $|Nom du fichier de définition de la fonctionnalité conteneur, tel que *Feature1. Feature*.|
|$SharePoint. Feature. FileNameWithoutExtension $|Nom du fichier de définition de fonctionnalité, sans l’extension de nom de fichier.|
|$SharePoint. Feature. DeploymentPath $|Nom du dossier qui contient la fonctionnalité dans le package. Ce jeton équivaut à la propriété « Deployment Path » dans le concepteur de fonctionnalités. Un exemple de valeur est, « Project1_Feature1 ».|
|$SharePoint. Feature.Id $|ID SharePoint de la fonctionnalité conteneur. Ce jeton, comme avec tous les jetons au niveau de la fonctionnalité, peut être utilisé uniquement par les fichiers inclus dans un package via une fonctionnalité, non ajouté directement à un package en dehors d’une fonctionnalité.|
|$SharePoint. ProjectItem.Name $|Nom de l’élément de projet (pas son nom de fichier), tel qu’il est obtenu à partir de **ISharePointProjectItem.Name**.|
|$SharePoint \<GUID> . type.. AssemblyQualifiedName $|Nom qualifié d’assembly du type qui correspond au [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] du jeton. Le format de [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] est en minuscule et correspond au format GUID. ToString ("D") (autrement dit, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|
|$SharePoint \<GUID> . type.. FullName $|Nom complet du type correspondant au GUID dans le jeton. Le format du GUID est en minuscules et correspond au format GUID. ToString ("D") (autrement dit, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Ajouter des extensions à la liste des extensions de fichier de remplacement de jeton
 Bien que les jetons puissent théoriquement être utilisés par tout fichier qui appartient à un élément de projet SharePoint inclus dans le package, par défaut, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] recherche les jetons uniquement dans les fichiers de package, les fichiers manifeste et les fichiers qui ont les extensions suivantes :

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- WebPart

- DWP

  Ces extensions sont définies par l' `<TokenReplacementFileExtensions>` élément dans le fichier Microsoft. VisualStudio. SharePoint. targets, situé dans le dossier... \\<Program Files \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools.

  Toutefois, vous pouvez ajouter des extensions de fichier supplémentaires à la liste. Ajoutez un `<TokenReplacementFileExtensions>` élément à n’importe quel PropertyGroup du fichier projet SharePoint qui est défini avant le \<Import> du fichier de cibles SharePoint.

> [!NOTE]
> Étant donné que le remplacement de jeton se produit après la compilation d’un projet, vous ne devez pas ajouter d’extensions de fichier pour les types de fichiers qui sont compilés, tels que *. cs*, *. vb* ou *. resx*. Les jetons sont remplacés uniquement dans les fichiers qui ne sont pas compilés.

 Par exemple, pour ajouter les extensions de nom de fichier (*. MyExtension* et *. yourextension*) à la liste des extensions de nom de fichier de remplacement de jeton, vous devez ajouter le code suivant à un fichier projet (*. csproj*) :

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

 Vous pouvez ajouter l’extension directement au fichier de cibles (*. targets*). Toutefois, l’ajout de l’extension modifie la liste des extensions pour tous les projets SharePoint empaquetés sur le système local, et pas seulement les vôtres. Cette extension peut être pratique lorsque vous êtes le seul développeur du système ou si la plupart de vos projets en ont besoin. Toutefois, étant donné qu’il s’agit d’une solution propre au système, cette approche n’est pas portable et, par conséquent, il est recommandé d’ajouter des extensions au fichier projet à la place.

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
