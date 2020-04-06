---
title: ProjectCollection Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12a22ca28c90ed1df69529ed3004b417b5e04276
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701974"
---
# <a name="projectcollection-element-visual-studio-templates"></a>Élément ProjectCollection (modèles Visual Studio)
Spécifie l'organisation et le contenu de modèles à plusieurs projets.

 \<VSTemplate> \<TemplateContent> \<ProjectCollection>

## <a name="syntax"></a>Syntaxe

```xml
<ProjectCollection>
    <ProjectTemplateLink> ... </ProjectTemplateLink>
    <SolutionFolder> ... </SolutionFolder>
</ProjectCollection>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie un projet dans un modèle multi-projets.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Groupe des projets dans des modèles à plusieurs projets.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie le contenu du modèle.|

## <a name="remarks"></a>Notes
 Les modèles à plusieurs projets jouent le rôle de conteneurs pour au moins deux projets. L’élément `ProjectCollection` est utilisé pour spécifier les projets à contenir dans le modèle. Pour plus d’informations sur les modèles multi-projets, voir [Comment : Créer des modèles multi-projets](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Exemple
 Cet exemple montre un fichier root *.vstemplate* à base multi-projet simple. Dans cet exemple, le modèle contient deux projets, `My Windows Application` et `My Class Library`. L'attribut `ProjectName` de l'élément `ProjectTemplateLink` définit le nom à assigner au projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si `ProjectName` l’attribut n’existe pas, le nom du fichier *.vstemplate* est utilisé comme nom du projet.

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
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Comment : Créer des modèles multi-projets](../ide/how-to-create-multi-project-templates.md)
