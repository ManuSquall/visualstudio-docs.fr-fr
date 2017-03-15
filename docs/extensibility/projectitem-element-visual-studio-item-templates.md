---
title: "ProjectItem, &#233;l&#233;ment (mod&#232;les d&#39;&#233;l&#233;ment Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> (élément de modèles d'élément Visual Studio)"
  - "ProjectItem (élément de modèles d'élément Visual Studio)"
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# ProjectItem, &#233;l&#233;ment (mod&#232;les d&#39;&#233;l&#233;ment Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie un fichier inclus dans le modèle d'élément.  
  
> [!NOTE]
>  L'élément `ProjectItem` accepte des attributs différents selon que le modèle concerne un projet ou un élément.  Cette rubrique explique l'élément `ProjectItem`.  Pour une explication de l'élément `ProjectItem` dans le cas de modèles de modèles de projet, consultez [ProjectItem, élément \(modèles de projet Visual Studio\)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
## Syntaxe  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`SubType`|Attribut facultatif.<br /><br /> Spécifie le sous\-type d'un élément dans un modèle à plusieurs fichiers.  Cette valeur détermine l'éditeur qu'utilisera [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour ouvrir l'élément.|  
|`CustomTool`|Attribut facultatif.<br /><br /> Définit le CustomTool pour l'élément dans le fichier projet.|  
|`ItemType`|Attribut facultatif.<br /><br /> Définit le ItemType pour l'élément dans le fichier projet.|  
|`ReplaceParameters`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si l'élément contient des paramètres dont les valeurs doivent être remplacées lorsqu'un projet est créé à partir du modèle.  La valeur par défaut est `false`|  
|`TargetFileName`|Attribut facultatif.<br /><br /> Spécifie le nom de l'élément créé à partir du modèle.  Cet attribut permet d'utiliser le remplacement de paramètre pour créer un nom d'élément.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Spécifie le contenu du modèle.|  
  
## Valeur texte  
 Une valeur texte est requise.  
  
 `string` qui représente le nom d'un fichier dans le fichier .zip du modèle.  
  
## Notes  
 `ProjectItem` est un enfant facultatif de `TemplateContent`.  
  
 L'attribut `TargetFileName` permet de renommer des fichiers à l'aide de paramètres.  Par exemple, si le fichier `MyFile.vb` existe dans le répertoire racine du fichier .zip du modèle et si vous souhaitez lui attribuer un nom basé sur celui que contient la boîte de dialogue **Ajouter un nouvel élément**, utilisez le XML suivant :  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Si vous créez un élément selon ce modèle, le nom du fichier correspond au nom entré dans la boîte de dialogue **Ajouter un nouvel élément**.  Cela s'avère utile lors de la création de modèles d'élément à plusieurs fichiers.  Pour plus d'informations, consultez [Comment : créer des modèles d'élément multifichier](../ide/how-to-create-multi-file-item-templates.md) et [Paramètres de modèle](../ide/template-parameters.md).  
  
## Exemple  
 L'exemple suivant illustre les métadonnées d'un modèle d'élément standard pour une classe [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Comment : créer des modèles d'élément multifichier](../ide/how-to-create-multi-file-item-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)