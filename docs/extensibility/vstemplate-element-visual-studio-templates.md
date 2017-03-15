---
title: "VSTemplate, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate"
helpviewer_keywords: 
  - "VSTemplate (élément de modèles de projet Visual Studio)"
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# VSTemplate, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient toutes les métadonnées du modèle de projet ou d'élément ou du Starter Kit.  
  
## Syntaxe  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Type`|Identifie le modèle en tant que modèle de projet ou modèle d'élément.  Cet attribut peut avoir la valeur `Project` ou `Item`.|  
|`Version`|Spécifie le numéro de version du modèle.  Les modèles dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] et l' [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ont une valeur d'attribut d' `Version` d' `3.0.0`.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie des données qui classent le modèle dans une catégorie et définit la façon dont il s'affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie le contenu du modèle.|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Élément facultatif.|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Élément facultatif.|  
  
### Éléments parents  
 Aucun  
  
## Notes  
 L'élément `VSTemplate` est l'élément racine des fichiers .vstemplate.  
  
## Exemple  
 L'exemple suivant affiche les métadonnées d'un modèle de projet pour une application [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
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
            <ProjectItem>Form1.cs</ProjectItem>  
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
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)