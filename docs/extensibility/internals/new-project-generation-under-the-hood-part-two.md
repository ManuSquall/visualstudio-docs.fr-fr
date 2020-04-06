---
title: 'Nouvelle génération de projets : Sous le capot, deuxième partie Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707024"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Génération de nouveau projet : les rouages du système, partie 2

Dans [New Project Generation: Under the Hood, La première partie,](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) nous avons vu comment la boîte de dialogue **du nouveau projet** est peuplée. Supposons que vous avez sélectionné une **application Windows Visual C,** rempli les boîtes de texte **nom** et **localisation,** et cliqué sur OK.

## <a name="generating-the-solution-files"></a>Génération des fichiers solutions
 Le choix d’un modèle d’application permet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de décompresser et d’ouvrir le fichier .vstemplate correspondant, et de lancer un modèle pour interpréter les commandes XML dans ce fichier. Ces commandes créent des projets et des éléments de projet dans la solution nouvelle ou existante.

 Le modèle déballe les fichiers source, appelés modèles d’éléments, à partir du même dossier .zip qui détient le fichier .vstemplate. Le modèle copie ces fichiers au nouveau projet, les personnalisant en conséquence.

### <a name="template-parameter-replacement"></a>Remplacement du paramètre de modèle
 Lorsque le modèle copie un modèle d’élément à un nouveau projet, il remplace tous les paramètres du modèle par des chaînes pour personnaliser le fichier. Un paramètre de modèle est un jeton spécial qui est précédé et suivi d’un signe en dollars, par exemple, $date$.

 Examinons un modèle d’élément de projet typique. Extraire et examiner Program.cs dans le dossier De programme Files-Microsoft Visual Studio 8-Common7-IDE-ProjectTemplates-CSharp-Windows.1033-WindowsApplication.zip.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

Si vous créez un nouveau projet d’application `$safeprojectname$` Windows nommé Simple, le modèle remplace le paramètre par le nom du projet.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 Pour obtenir une liste exhaustive des paramètres de modèle, consultez [Paramètres de modèle](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Un regard à l’intérieur d’un . Fichier VSTemplate
 Un fichier de base .vstemplate a ce format

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Nous avons \<examiné la section TemplateData> dans la [nouvelle génération de projet : Sous le capot, première partie.](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) Les balises de cette section sont utilisées pour contrôler l’apparence de la boîte de dialogue **du nouveau projet.**

 Les balises de la \<section TemplateContent> contrôlent la génération de nouveaux projets et éléments de projet. Voici la \<section TemplateContent> du fichier cswindowsapplication.vstemplate dans le dossier «Program Files-Microsoft Visual Studio 8-Common7-IDE-ProjectTemplates-CSharp-Windows-1033-WindowsApplication.zip».

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 L’étiquette \<Project> contrôle la production d’un projet, et l’étiquette \<ProjectItem> contrôle la génération d’un élément de projet. Si le paramètre ReplaceParameters est vrai, le modèle personnalisera tous les paramètres du modèle dans le fichier ou l’élément du projet. Dans ce cas, tous les éléments du projet sont personnalisés, à l’exception de Paramètres.

 Le paramètre TargetFileName spécifie le nom et le parcours relatif du fichier ou de l’élément de projet qui en résulte. Cela vous permet de créer une structure de dossier pour votre projet. Si vous ne spécifiez pas cet argument, l’élément du projet portera le même nom que le modèle d’élément du projet.

 La structure de dossier d’application Windows qui en résulte ressemble à ceci :

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 La première \<et unique étiquette de> du projet dans le modèle se lit comme suit :

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Cela demande au modèle New Project de créer le fichier de projet Simple.csproj en copiant et en personnalisant le modèle windowsapplication.csproj.

### <a name="designers-and-references"></a>Designers et Références
 Vous pouvez voir dans le Solution Explorer que le dossier Propriétés est présent et contient les fichiers attendus. Mais qu’en est-il des références de projets et des dépendances de fichiers de concepteur, telles que Resources.Designer.cs à Resources.resx, et Form1.Designer.cs à Form1.cs?  Ceux-ci sont configurés dans le fichier Simple.csproj lorsqu’il est généré.

 Voici le \<> ItemGroup de Simple.csproj qui crée les références du projet :

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Vous pouvez voir que ce sont les six références de projet qui apparaissent dans l’Explorer Solution. Voici une section d’un autre \<itemGroup>. De nombreuses lignes de code ont été supprimées pour plus de clarté. Cette section rend Settings.Designer.cs dépendante de Paramètres.paramètres :

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Voir aussi

- [Génération de nouveau projet : les rouages du système, partie 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
