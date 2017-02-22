---
title: "ProjectTemplateLink, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink"
helpviewer_keywords: 
  - "<ProjectTemplateLink> (élément de modèles Visual Studio)"
  - "ProjectTemplateLink (élément de modèles Visual Studio)"
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# ProjectTemplateLink, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie le chemin d'accès au fichier .vstemplate d'un projet dans un modèle à plusieurs projets.  
  
## Syntaxe  
  
```  
<ProjectTemplateLink ProjectName="Name">     PathToTemplateFile </ProjectTemplateLink>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`ProjectName`|Attribut facultatif.<br /><br /> Spécifie le nom de chaque projet individuel dans un modèle à plusieurs projets.  La boîte de dialogue **Nouveau projet** ne peut pas assigner de noms à des projets individuels.|  
|`CopyParameters`|Permet à toutes les variables du modèle de groupe principal d'être copiées sur chaque modèle lié.<br /><br /> Les paramètres des modèles liés ont un préfixe `"$ext_*$"`.  Par exemple, si dans le modèle de groupe parent le paramètre `$projectname$` a une valeur ExampleProject1, lorsque le modèle lié doit être exécuté à son tour, il acquiert un paramètre `$ext_projectname$`, qui est une copie du paramètre `$projectname$` du modèle de groupe parent.<br /><br /> Cela permet aux modèles liés de partager des paramètres communs, qui peuvent être aisément créés uniquement dans le modèle de groupe parent.<br /><br /> Cet attribut est facultatif, et il prend automatiquement la valeur `false` par défaut lorsqu'il n'est pas inclus.<br /><br /> Introduit pour la première fois dans Visual Studio 2013 Update 2.  Pour référencer la version de produit appropriée, consultez [Referencing Assemblies Delivered in the Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/fr-fr/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Spécifie l'organisation et le contenu de modèles à plusieurs projets.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Groupe des projets dans des modèles à plusieurs projets.|  
  
## Valeur texte  
 Une valeur texte est requise.  
  
 Ce texte spécifie le chemin d'accès au fichier .vstemplate du modèle.  
  
## Notes  
 Les modèles à plusieurs projets jouent le rôle de conteneurs pour au moins deux projets.  L'élément `ProjectTemplateLink` spécifie l'emplacement du fichier .vstemplate pour l'un des projets du modèle.  Le fichier .vstemplate d'un modèle à plusieurs projets contient un élément `ProjectTemplateLink` par projet du modèle.  Pour plus d'informations sur les modèles à plusieurs projets, consultez [Comment : créer des modèles à plusieurs projets](../ide/how-to-create-multi-project-templates.md).  
  
## Exemple  
 Cet exemple illustre un fichier .vstemplate racine simple pour un modèle à plusieurs projets.  Dans cet exemple, le modèle contient deux projets, `My Windows Application` et `My Class Library`.  L'attribut `ProjectName` de l'élément `ProjectTemplateLink` définit le nom à assigner au projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si l'attribut `ProjectName` n'existe pas, le nom du fichier .vstemplate est utilisé comme nom du projet.  
  
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
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Comment : créer des modèles à plusieurs projets](../ide/how-to-create-multi-project-templates.md)