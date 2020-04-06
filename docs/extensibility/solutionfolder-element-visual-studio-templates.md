---
title: Élément SolutionFolder (Modèles de studio visuel) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3262a5dcc0f226a0ac1b3aa08219fb89dbf70e83
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700002"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>SolutionFolder, élément (modèles Visual Studio)
Groupe des projets dans des modèles à plusieurs projets.

 \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder>

## <a name="syntax"></a>Syntaxe

```
<SolutionFolder Name="DirectoryName">
    ...
</SolutionFolder>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Name`|Attribut requis.<br /><br /> Nom du dossier solution.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie le chemin d'accès au fichier .vstemplate d'un projet dans un modèle à plusieurs projets.|
|`SolutionFolder`|Élément facultatif.<br /><br /> Groupe des projets dans des modèles à plusieurs projets.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Spécifie l'organisation et le contenu de modèles à plusieurs projets.|
|`SolutionFolder`|Groupe des projets dans des modèles à plusieurs projets.|

## <a name="remarks"></a>Notes
 Les modèles à plusieurs projets jouent le rôle de conteneurs pour au moins deux projets. L'élément `SolutionFolder` permet d'organiser les projets du modèle par groupes. Les dossiers spécifiés par les éléments `SolutionFolder` sont créés comme dossiers de solution du projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations sur les modèles multi-projets, voir [Comment : Créer des modèles multi-projets](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Exemple
 Cet exemple utilise l'élément `SolutionFolder` pour répartir le modèle à plusieurs projets en deux groupes, `Math Classes` et `Graphics Classes`. Le modèle contient quatre projets, dont deux sont placés dans chaque dossier de solution.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Guide pratique pour créer des modèles à plusieurs projets](../ide/how-to-create-multi-project-templates.md)
