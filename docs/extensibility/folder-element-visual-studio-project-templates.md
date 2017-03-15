---
title: "Folder, &#233;l&#233;ment (mod&#232;les de projet Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Folder"
helpviewer_keywords: 
  - "Folder (élément de modèles de projet Visual Studio)"
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Folder, &#233;l&#233;ment (mod&#232;les de projet Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie un dossier à ajouter au projet.  
  
## Syntaxe  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Attribut requis.<br /><br /> Nom du dossier du projet.|  
|`TargetFolderName`|Attribut facultatif.<br /><br /> Spécifie le nom à donner au dossier lorsqu'un projet est créé à partir du modèle.  Cet attribut permet d'utiliser le remplacement de paramètres pour créer un nom du dossier ou attribuer un nom à un dossier avec une chaîne internationale qui ne peut pas être utilisée directement dans le fichier .zip.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`Folder`|Spécifie un dossier à ajouter au projet.  Les éléments `Folder` peuvent contenir des éléments `Folder` enfants.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Spécifie un fichier à ajouter au projet.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../extensibility/project-element-visual-studio-templates.md)|Élément enfant facultatif de [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## Notes  
 `Folder` est un enfant facultatif de `Project`.  
  
 Vous pouvez utiliser une des méthodes suivantes pour organiser des éléments de projet en dossiers dans un modèle :  
  
-   Incluez les dossiers dans le fichier .zip du modèle et ajoutez\-les au projet dans le fichier .vstemplate en spécifiant le chemin d'accès au fichier dans les éléments `ProjectItem`, sans éléments `Folder`.  C'est la méthode conseillée.  Par exemple :  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Incluez les dossiers dans le fichier .zip du modèle et ajoutez\-les au projet dans le fichier .vstemplate avec les éléments `Folder`.  Par exemple :  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   N'incluez pas de dossiers dans le fichier .zip du modèle, mais ajoutez des dossiers à l'aide de l'attribut `TargetFileName` de l'élément `ProjectItem`.  Par exemple :  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## Exemple  
 L'exemple suivant affiche les métadonnées d'un modèle de projet pour une application Windows [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [ProjectItem, élément \(modèles d'élément Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)