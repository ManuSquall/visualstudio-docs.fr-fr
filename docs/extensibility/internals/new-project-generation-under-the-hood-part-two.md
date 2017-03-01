---
title: "Nouvelle génération de projet : Dans les coulisses, deuxième partie | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c5f214774a5cf0aeb3896004632f8a2076782b14
ms.lasthandoff: 02/22/2017

---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nouvelle génération de projet : Dans les coulisses, deuxième partie
Dans [nouvelle génération de projet : rouages du système, une partie](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) que nous avons vu comment la **nouveau projet** boîte de dialogue est alimentée. Supposons que vous avez sélectionné un **Application Windows Visual C#**, rempli le **nom** et **emplacement** zones de texte et cliquez sur OK.  
  
## <a name="generating-the-solution-files"></a>Génération des fichiers de Solution  
 Choix d’un modèle d’application dirige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour décompresser et ouvrir le fichier .vstemplate correspondant et lancer un modèle pour interpréter les commandes XML dans ce fichier. Ces commandes créent des projets et des éléments de projet dans la solution nouvelle ou existante.  
  
 Le modèle décompresse les fichiers sources, appelés modèles d’élément, à partir du même dossier .zip qui contient le fichier .vstemplate. Le modèle copie ces fichiers dans le nouveau projet, leur personnalisation en conséquence. Pour une vue d’ensemble des modèles de projet et d’élément, consultez [NIB : modèles Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Remplacement de paramètre de modèle  
 Lorsque le modèle copie un modèle d’élément à un nouveau projet, il remplace les paramètres de modèle avec des chaînes pour personnaliser le fichier. Un paramètre de modèle est un jeton spécial qui est précédé et suivi d’un signe dollar, par exemple $date$.  
  
 Nous allons examiner un modèle d’élément de projet standard. Extraire et examiner le fichier Program.cs dans le dossier 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip Program Files\Microsoft Visual Studio.  
  
```  
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
  
 Si vous créez un nouveau projet d’application Windows nommé Simple, le modèle remplace le `$safeprojectname$` paramètre avec le nom du projet.  
  
```  
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
  
 Pour obtenir une liste complète des paramètres de modèle, consultez la page [les paramètres de modèle](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Un coup de œil à l’intérieur d’un. Fichier VSTemplate  
 Un fichier .vstemplate de base a ce format  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Nous avons étudié le \<TemplateData > section dans le [nouvelle génération de projet : rouages du système, une partie](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Les balises de cette section sont utilisés pour contrôler l’apparence de la **nouveau projet** boîte de dialogue.  
  
 Les balises dans le \<TemplateContent > section contrôle la génération de nouveaux projets et éléments de projet. Voici le \<TemplateContent > section à partir du fichier cswindowsapplication.vstemplate dans le dossier \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
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
  
 Le \<projet > balise contrôle la génération d’un projet et le \<ProjectItem > balise contrôle la génération d’un projet. Si le paramètre ReplaceParameters est true, le modèle sera personnaliser tous les paramètres de modèle dans le fichier de projet ou l’élément. Dans ce cas, tous les éléments de projet sont personnalisés, à l’exception Settings.settings.  
  
 Le paramètre TargetFileName Spécifie le nom et le chemin d’accès relatif du fichier de projet résultant ou élément. Cela vous permet de créer une structure de dossiers de votre projet. Si vous ne spécifiez pas cet argument, l’élément de projet aura le même nom que le modèle de projet.  
  
 La structure de dossiers d’application Windows résultante ressemble à ceci :  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 La première et la seule \<projet > balise dans les lectures du modèle :  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Cela fait en sorte que le modèle de projet pour créer le fichier de projet Simple.csproj en copiant et en personnalisant le windowsapplication.csproj d’élément de modèle.  
  
### <a name="designers-and-references"></a>Concepteurs et références  
 Vous pouvez voir dans l’Explorateur de solutions que le dossier des propriétés est présent et contient les fichiers attendus. Mais qu’en est-il de projet référence et des dépendances de fichier du concepteur, comme Resources.Designer.cs à Resources.resx et Form1.Designer.cs à Form1.cs ?  Ces paramétrées dans le fichier Simple.csproj lorsqu’il est généré.  
  
 Voici le \<ItemGroup > de Simple.csproj qui crée les références de projet :  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Vous pouvez voir que ce sont les références de six projet qui apparaissent dans l’Explorateur de solutions. Voici une section d’une autre \<ItemGroup >. Nombre de lignes de code ont été supprimée par souci de clarté. Cette section rend Settings.Designer.cs dépendante Settings.settings :  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nouvelle génération de projet : Dans les coulisses, partie&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild1.md)
