---
title: "ProjectItem, &#233;l&#233;ment (mod&#232;les de projet Visual&#160;Studio) | Microsoft Docs"
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
  - "<ProjectItem> (élément de modèles de projet Visual Studio)"
  - "ProjectItem (élément de modèles de projet Visual Studio)"
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# ProjectItem, &#233;l&#233;ment (mod&#232;les de projet Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie un fichier inclus dans le modèle de projet.  
  
> [!NOTE]
>  L'élément `ProjectItem` accepte des attributs différents selon que le modèle concerne un projet ou un élément.  Cette rubrique explique l'élément `ProjectItem` des modèles de projet.  Pour une explication de l'élément `ProjectItem` dans le cas de modèles d'élément, consultez [ProjectItem, élément \(modèles d'élément Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
## Syntaxe  
  
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
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`TargetFileName`|Attribut facultatif.<br /><br /> Spécifie le nom et le chemin d'accès de l'élément de projet lorsqu'un projet est créé à partir du modèle.  Cet attribut est utile pour créer une structure de répertoires différente de celle du fichier .zip du modèle ou pour utiliser le remplacement de paramètre pour créer un nom d'élément.|  
|`ReplaceParameters`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si l'élément contient des paramètres dont les valeurs doivent être remplacées lorsqu'un projet est créé à partir du modèle.  La valeur par défaut est `false`|  
|`OpenInEditor`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si l'élément doit être ouvert dans son éditeur respectif dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lorsqu'un projet est créé à partir du modèle.<br /><br /> Les attributs `OpenInWebBrowser` et `OpenInHelpBrowser` sont ignorés sur un élément dont `OpenInEditor` a la valeur `true`.<br /><br /> La valeur par défaut est `false`.|  
|`OpenInWebBrowser`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si l'élément doit être ouvert dans le Navigateur Web lorsqu'un projet est créé à partir du modèle.<br /><br /> Seuls les fichiers HTML et fichiers texte locaux du projet peuvent être ouverts dans le Navigateur Web.  Les URL externes ne peuvent pas être ouvertes avec cet attribut.<br /><br /> La valeur par défaut est `false`.|  
|`OpenInHelpBrowser`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si l'élément doit être ouvert dans la visionneuse de l'aide lorsqu'un projet est créé à partir du modèle.<br /><br /> Seuls les fichiers HTML et texte locaux du projet peuvent être ouverts dans le navigateur d'aide.  Les URL externes ne peuvent pas être ouvertes avec cet attribut.<br /><br /> La valeur par défaut est `false`.|  
|`OpenOrder`|Attribut facultatif.<br /><br /> Spécifie une valeur numérique qui représente l'ordre dans lequel les éléments seront ouverts dans leurs éditeurs respectifs.  Toutes les valeurs doivent être des multiples de 10.  Les éléments avec des valeurs supérieures d' `OpenOrder` sont ouverts en premier.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../extensibility/project-element-visual-studio-templates.md)|Spécifie les fichiers ou répertoires à ajouter au projet.|  
  
## Valeur texte  
 Une valeur texte est requise.  
  
 `string` qui représente le nom d'un fichier contenu dans le fichier .zip du modèle, ou son chemin d'accès.  
  
## Notes  
 `ProjectItem` est un enfant facultatif de `Project`.  
  
 L'attribut `TargetFileName` peut être utilisé pour créer une structure de répertoires différente de la structure de répertoires du fichier .zip du modèle.  Par exemple, si le fichier `MyFile.vb` existe à la racine du fichier .zip du modèle alors que vous souhaitez le placer dans un répertoire nommé `CustomFiles` dans tous les projets créés à partir du modèle, utilisez le XML suivant :  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 L'attribut `TargetFileName` peut également être utilisé pour renommer les fichiers dont le nom contient des caractères internationaux.  Par exemple, un modèle de fichier .zip ne peut pas contenir de noms de fichiers avec des caractères Unicode ; par conséquent, le fichier doit être renommé pour pouvoir être compressé dans un fichier .zip.  L'attribut `TargetFileName` peut être utilisé pour rétablir le nom de fichier Unicode d'origine.  
  
 L'attribut `TargetFileName` permet également de renommer des fichiers à l'aide de paramètres.  La procédure suivante explique comment renommer le fichier `MyFile.vb`, qui existe dans le répertoire racine du fichier modèle .zip, en un nom de fichier basé sur le nom du projet.  
  
### Pour renommer des fichiers avec des paramètres  
  
1.  Utilisez le code XML suivant dans le fichier .vstemplate :  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Ouvrez le fichier projet \(.vbproj pour un projet [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] \) dans un éditeur de texte ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Recherchez la ligne du fichier projet qui ressemble au code XML suivant :  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Remplacez la ligne de code par la ligne XML suivante :  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     À la création d'un projet à partir de ce modèle, le fichier prend un nom basé sur celui que l'utilisateur a entré dans la boîte de dialogue **Nouveau projet**, et dont tous les caractères et espaces potentiellement dangereux ont été supprimés.  Pour plus d’informations, consultez [Paramètres de modèle](../ide/template-parameters.md).  
  
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
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [ProjectItem, élément \(modèles d'élément Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)