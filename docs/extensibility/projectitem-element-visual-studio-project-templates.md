---
title: ProjectItem Element (Visual Studio Project Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11052d8e585f1d06f6d787402001cfbbe2b6810f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701839"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Élément ProjectItem (modèles de projets Visual Studio)
Spécifie un fichier qui est inclus dans le modèle de projet.

> [!NOTE]
> L’élément `ProjectItem` accepte différents attributs selon que le modèle est pour un projet ou un élément. Ce sujet `ProjectItem` explique l’élément des modèles de projet. Pour une explication `ProjectItem` de l’élément pour les modèles d’éléments, voir [ProjectItem Element (Visual Studio Item Templates)](../extensibility/projectitem-element-visual-studio-item-templates.md).

 \<VSTemplate> \<Projet>> \< \<ProjectItem>

## <a name="syntax"></a>Syntaxe

```
<ProjectItem
    TargetFileName="TargetFileName.ext"
    ReplaceParameters="true/false"
    OpenInEditor="true/false"
    OpenInWebBrowser="true/false"
    OpenInHelpBrowser="true/false"
    OpenOrder="Value">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

| Attribut | Description |
|---------------------| - |
| `TargetFileName` | Attribut facultatif.<br /><br /> Spécifie le nom et le chemin de l’élément du projet lorsqu’un projet est créé à partir du modèle. Cet attribut est utile pour créer une structure d’annuaire différente de la structure d’annuaire dans le fichier *.zip* modèle, ou pour l’utilisation du remplacement de paramètres pour créer un nom d’élément. |
| `ReplaceParameters` | Attribut facultatif.<br /><br /> Une valeur Boolean qui précise si l’élément a des valeurs de paramètres qui doivent être remplacées lorsqu’un projet est créé à partir du modèle. La valeur par défaut est `false`. |
| `OpenInEditor` | Attribut facultatif.<br /><br /> Une valeur Boolean qui précise si l’élément doit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] être ouvert dans son éditeur respectif dans le moment où un projet est créé à partir du modèle.<br /><br /> Les `OpenInWebBrowser` `OpenInHelpBrowser` attributs et les attributs `OpenInEditor` sont `true`ignorés sur un élément avec une valeur de .<br /><br /> La valeur par défaut est `false`. |
| `OpenInWebBrowser` | Attribut facultatif.<br /><br /> Une valeur Boolean qui précise si l’élément doit être ouvert le navigateur Web lorsqu’un projet est créé à partir du modèle.<br /><br /> Seuls les fichiers HTML et les fichiers texte locaux au projet peuvent être ouverts dans le navigateur Web. Les URL externes ne peuvent pas être ouvertes avec cet attribut.<br /><br /> La valeur par défaut est `false`. |
| `OpenInHelpBrowser` | Attribut facultatif.<br /><br /> Une valeur Boolean qui précise si l’élément doit être ouvert dans le visualiseur d’aide lorsqu’un projet est créé à partir du modèle.<br /><br /> Seuls les fichiers HTML et les fichiers texte locaux au projet peuvent être ouverts dans le navigateur Help. Les URL externes ne peuvent pas être ouvertes avec cet attribut.<br /><br /> La valeur par défaut est `false`. |
| `OpenOrder` | Attribut facultatif.<br /><br /> Spécifie une valeur numérique qui représente l’ordre d’ouverture des articles dans leurs éditeurs respectifs. Toutes les valeurs doivent être multiples de 10. Les articles `OpenOrder` avec des valeurs plus élevées sont ouverts en premier. |

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Projet](../extensibility/project-element-visual-studio-templates.md)|Spécifie les fichiers ou les répertoires à ajouter au projet.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Un `string` qui représente le nom ou le chemin vers un fichier dans le fichier *.zip* modèle.

## <a name="remarks"></a>Notes
 `ProjectItem`est un enfant `Project`optionnel de .

 L’attribut `TargetFileName` peut être utilisé pour créer une structure d’annuaire différente de la structure d’annuaire dans le fichier *.zip* modèle. Par exemple, si le fichier *MyFile.vb* existe dans la racine du fichier *.zip* modèle, mais vous voulez que le fichier soit placé dans un répertoire nommé *CustomFiles* dans tous les projets créés à partir du modèle, vous utiliseriez le XML suivant :

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 L’attribut `TargetFileName` peut également être utilisé pour renommer les fichiers qui contiennent des caractères internationaux dans leurs noms de fichiers. Par exemple, un fichier *template .zip* ne peut pas contenir les noms de fichiers avec des caractères Unicode, de sorte que le fichier doit être renommé avant qu’il puisse être compressé dans un fichier *.zip.* L’attribut `TargetFileName` peut être utilisé pour définir le nom de fichier à l’original Unicode nom de fichier.

 L’attribut `TargetFileName` peut également être utilisé pour renommer les fichiers avec des paramètres. La procédure suivante explique comment renommer le fichier *MyFile.vb*, qui existe dans le répertoire racine du fichier *.zip* modèle, à un nom de fichier basé sur le nom du projet.

### <a name="to-rename-files-with-parameters"></a>Renommer les fichiers avec paramètres

1. Utilisez le XML suivant dans le fichier *.vstemplate* :

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Ouvrez le fichier de projet *(.vbproj* pour un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projet) dans un éditeur de texte ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

3. Localiser la ligne dans le fichier du projet qui ressemble à la XML suivante :

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Remplacer la ligne de code par le XML suivant :

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Lorsqu’un projet est créé à partir de ce modèle, le nom du fichier est basé sur le nom que l’utilisateur a inscrit dans la boîte de dialogue **du nouveau projet,** avec tous les caractères et espaces dangereux supprimés. Pour plus d’informations, voir [Paramètres Template](../ide/template-parameters.md).

## <a name="example"></a>Exemple
 L’exemple suivant montre les métadonnées [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] d’un modèle de projet pour une application.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Élément ProjectItem (modèles d’objets Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
