---
title: ProjectTemplateLink Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6d402b6605f2e01a20d400c2c33573c686a1cdd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701818"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink, élément (modèles Visual Studio)
Spécifie le chemin vers le fichier *.vstemplate* d’un projet dans un modèle multi-projet.

 \<VSTemplate \<> TemplateContent> \<ProjectCollection> \<ProjectTemplateLink> -ou- \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder> \<ProjectTemplateLink>

## <a name="syntax"></a>Syntaxe

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`ProjectName`|Attribut facultatif.<br /><br /> Spécifie le nom de chaque projet individuel dans un modèle à plusieurs projets. La boîte de dialogue **du nouveau projet** ne peut pas attribuer des noms à des projets individuels.|
|`CopyParameters`|Permet à toutes les variables du modèle de groupe principal d'être copiées sur chaque modèle lié.<br /><br /> Les paramètres des modèles liés ont un préfixe `"$ext_*$"`. Par exemple, si dans le `$projectname$` modèle du groupe parent le paramètre a une valeur **ExempleProject1**, `$ext_projectname$`lorsque le modèle `$projectname$` lié obtient son tour pour être exécuté, il acquiert un paramètre , qui est une copie du paramètre à partir du modèle de groupe parent.<br /><br /> Cela permet aux modèles liés de partager des paramètres communs, qui peuvent être aisément créés uniquement dans le modèle de groupe parent.<br /><br /> Cet attribut est facultatif, et il prend automatiquement la valeur `false` par défaut lorsqu'il n'est pas inclus.<br /><br /> Introduit pour la première fois dans Visual Studio 2013 Update 2. Pour référencer la bonne version du produit, voir [les assemblages de référence livrés dans la mise à jour SDK 2013 de Visual Studio 2013](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Spécifie l'organisation et le contenu de modèles à plusieurs projets.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Groupe des projets dans des modèles à plusieurs projets.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Ce texte spécifie le chemin vers le fichier *.vstemplate* du modèle.

## <a name="remarks"></a>Notes
 Les modèles à plusieurs projets jouent le rôle de conteneurs pour au moins deux projets. L’élément `ProjectTemplateLink` est utilisé pour spécifier l’emplacement du fichier *.vstemplate* pour l’un des projets du modèle. Le fichier *.vstemplate* d’un modèle `ProjectTemplateLink` multi-projet contient un élément pour chaque projet dans le modèle. Pour plus d’informations sur les modèles multi-projets, voir [Comment : Créer des modèles multi-projets](../ide/how-to-create-multi-project-templates.md).

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
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
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
