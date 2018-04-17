---
title: ProjectTemplateLink, élément (modèles Visual Studio) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10ebc56e03a6582ab37126097db5f79ed9c5f2a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink, élément (modèles Visual Studio)
Spécifie le chemin d’accès au fichier .vstemplate d’un projet dans un modèle à plusieurs projets.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<ProjectTemplateLink >  
- ou -  
\<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<SolutionFolder >  
 \<ProjectTemplateLink >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ProjectTemplateLink ProjectName="Name">  
    PathToTemplateFile  
</ProjectTemplateLink>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`ProjectName`|Attribut facultatif.<br /><br /> Spécifie le nom de chaque projet individuel dans un modèle à plusieurs projets. Le **nouveau projet** boîte de dialogue ne peut pas assigner de noms à des projets individuels.|  
|`CopyParameters`|Permet à toutes les variables du modèle de groupe principal d'être copiées sur chaque modèle lié.<br /><br /> Les paramètres des modèles liés ont un préfixe `"$ext_*$"`. Par exemple, si dans le modèle de groupe parent le paramètre `$projectname$` a la valeur **ExampleProject1**, lorsque le modèle lié obtient son tour pour être exécutée, il acquiert un paramètre `$ext_projectname$`, qui est une copie de la `$projectname$`paramètre à partir du modèle de groupe parent.<br /><br /> Cela permet aux modèles liés de partager des paramètres communs, qui peuvent être aisément créés uniquement dans le modèle de groupe parent.<br /><br /> Cet attribut est facultatif, et il prend automatiquement la valeur `false` par défaut lorsqu'il n'est pas inclus.<br /><br /> Introduit pour la première fois dans Visual Studio 2013 Update 2. Pour faire référence à la version de produit correct, consultez [faisant référence à des assemblys remis dans Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Spécifie l'organisation et le contenu de modèles à plusieurs projets.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Groupe des projets dans des modèles à plusieurs projets.|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Ce texte spécifie le chemin d’accès au fichier .vstemplate du modèle.  
  
## <a name="remarks"></a>Notes  
 Les modèles à plusieurs projets jouent le rôle de conteneurs pour au moins deux projets. L'élément `ProjectTemplateLink` spécifie l'emplacement du fichier .vstemplate pour l'un des projets du modèle. Le fichier .vstemplate d'un modèle à plusieurs projets contient un élément `ProjectTemplateLink` par projet du modèle. Pour plus d’informations sur les modèles à projets multiples, consultez [Comment : créer des modèles à projets multiples](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre un fichier .vstemplate racine simple pour un modèle à plusieurs projets. Dans cet exemple, le modèle contient deux projets, `My Windows Application` et `My Class Library`. L'attribut `ProjectName` de l'élément `ProjectTemplateLink` définit le nom à assigner au projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si l'attribut `ProjectName` n'existe pas, le nom du fichier .vstemplate est utilisé comme nom du projet.  
  
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
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Guide pratique pour créer des modèles à plusieurs projets](../ide/how-to-create-multi-project-templates.md)