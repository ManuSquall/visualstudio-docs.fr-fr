---
title: 'Nouvelle génération de projet : Sous le capot, deuxième partie | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ccdd4cd8bafc4bc4a899ea47d62ec10e578569c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148202"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nouvelle génération de projet : Sous le capot, deuxième partie

Dans [nouvelle génération de projet : En coulisses, une partie](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) nous l’avons vu comment le **nouveau projet** boîte de dialogue boîte est remplie. Supposons que vous avez sélectionné un **Application Windows Visual c#**, renseigné le **nom** et **emplacement** zones de texte et cliquer sur OK.

## <a name="generating-the-solution-files"></a>Génération des fichiers de Solution
 Choix d’un modèle d’application dirige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à décompresser et ouvrir le fichier .vstemplate correspondant et de lancer un modèle pour interpréter les commandes XML dans ce fichier. Ces commandes créent des projets et éléments de projet dans la solution nouvelle ou existante.

 Le modèle décompresse les fichiers sources, appelés modèles d’élément, à partir du même dossier .zip qui contient le fichier .vstemplate. Le modèle copie ces fichiers dans le nouveau projet, leur personnalisation en conséquence.

### <a name="template-parameter-replacement"></a>Remplacement des paramètres de modèle
 Lorsque le modèle copie un modèle d’élément à un nouveau projet, il remplace les paramètres de modèle avec des chaînes pour personnaliser le fichier. Un paramètre de modèle est un jeton spécial qui est précédé et suivi d’un signe dollar, par exemple, un $date$.

 Examinons un modèle d’élément de projet standard. Extraire et examiner le fichier Program.cs dans le dossier 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip Program Files\Microsoft Visual Studio.

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

Si vous créez un nouveau projet d’application Windows nommé Simple, le modèle remplace le `$safeprojectname$` paramètre portant le nom du projet.

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

## <a name="a-look-inside-a-vstemplate-file"></a>Un coup de œil à l’intérieur d’un. Fichier VSTemplate
 Un fichier .vstemplate de base est au format

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Nous avons étudié le \<TemplateData > section dans le [nouvelle génération de projet : Sous le capot, première partie](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Les étiquettes dans cette section sont utilisées pour contrôler l’apparence de la **nouveau projet** boîte de dialogue.

 Les balises dans le \<TemplateContent > section contrôle la génération de nouveaux projets et éléments de projet. Voici le \<TemplateContent > section à partir du fichier cswindowsapplication.vstemplate dans le dossier \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

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

 Le \<projet > balise contrôle la génération d’un projet et le \<ProjectItem > balise contrôle la génération d’un élément de projet. Si le paramètre ReplaceParameters est true, le modèle sera personnaliser tous les paramètres de modèle dans le fichier projet ou l’élément. Dans ce cas, tous les éléments de projet sont personnalisés, à l’exception Settings.settings.

 Le paramètre TargetFileName Spécifie le nom et le chemin d’accès relatif du fichier de projet résultant ou élément. Cela vous permet de créer une structure de dossier pour votre projet. Si vous ne spécifiez pas cet argument, l’élément de projet aura le même nom que le modèle d’élément de projet.

 La structure de dossiers d’application Windows qui en résulte ressemble à ceci :

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 Le premier et unique \<projet > balise dans les lectures de modèle :

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Cela indique le modèle de projet pour créer le fichier de projet Simple.csproj en copiant et en personnalisant le windowsapplication.csproj d’élément de modèle.

### <a name="designers-and-references"></a>Concepteurs et références
 Vous pouvez voir dans l’Explorateur de solutions que le dossier Properties est présent et contient les fichiers attendus. Mais qu’en est-il de projet fait référence et les dépendances de fichier de concepteur, tels que Resources.Designer.cs à Resources.resx et Form1.Designer.cs pour Form1.cs ?  Ces paramétrées dans le fichier Simple.csproj lorsqu’il est généré.

 Voici le \<ItemGroup > à partir de Simple.csproj qui crée les références de projet :

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

 Vous pouvez voir que ce sont les références du projet de six qui apparaissent dans l’Explorateur de solutions. Voici une section d’un autre \<ItemGroup >. Nombre de lignes de code ont été supprimée par souci de clarté. De cette section, Settings.Designer.cs dépend Settings.settings :

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Voir aussi

- [Nouvelle génération de projet : Sous le capot, première partie](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)