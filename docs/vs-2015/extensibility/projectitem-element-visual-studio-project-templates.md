---
title: ProjectItem, élément (modèles de projet Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e08d08e8ec68e684ced1972f277af9b04805c3e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953741"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem, élément (modèles de projet Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie un fichier qui est inclus dans le modèle de projet.  
  
> [!NOTE]
>  Le `ProjectItem` élément accepte des attributs différents selon que le modèle est pour un projet ou un élément. Cette rubrique explique les `ProjectItem` , élément pour les modèles de projet. Pour obtenir une explication de la `ProjectItem` , élément pour les modèles d’élément, consultez [ProjectItem, élément (modèles d’élément Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Project>  
 \<ProjectItem>  
  
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
  
|Attribut|Description|  
|---------------|-----------------|  
|`TargetFileName`|Attribut facultatif.<br /><br /> Spécifie le nom et le chemin d’accès de l’élément de projet lorsqu’un projet est créé à partir du modèle. Cet attribut est utile pour la création d’une structure de répertoires différente de la structure de répertoires dans le fichier .zip du modèle, ou d’utiliser le remplacement de paramètre pour créer un nom d’élément.|  
|`ReplaceParameters`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si l’élément a des valeurs de paramètre qui doivent être remplacés lorsqu’un projet est créé à partir du modèle. La valeur par défaut est `false`.|  
|`OpenInEditor`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si l’élément doit être ouvert dans son éditeur respectif dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lorsqu’un projet est créé à partir du modèle.<br /><br /> Le `OpenInWebBrowser` et `OpenInHelpBrowser` attributs sont ignorés sur un élément avec un `OpenInEditor` valeur `true`.<br /><br /> La valeur par défaut est `false`.|  
|`OpenInWebBrowser`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si l’élément doit être ouvert le navigateur Web lorsqu’un projet est créé à partir du modèle.<br /><br /> Uniquement les fichiers HTML et les fichiers texte qui sont locaux du projet peuvent être ouverts dans le navigateur Web. URL externes ne peut pas être ouvert avec cet attribut.<br /><br /> La valeur par défaut est `false`.|  
|`OpenInHelpBrowser`|Attribut facultatif.<br /><br /> Une valeur booléenne qui spécifie si l’élément doit être ouvert dans la visionneuse d’aide lorsqu’un projet est créé à partir du modèle.<br /><br /> Uniquement les fichiers HTML et les fichiers texte qui sont locaux du projet peuvent être ouverts dans le navigateur d’aide. URL externes ne peut pas être ouvert avec cet attribut.<br /><br /> La valeur par défaut est `false`.|  
|`OpenOrder`|Attribut facultatif.<br /><br /> Spécifie une valeur numérique qui représente l’ordre que les éléments seront ouverts dans leurs éditeurs respectifs. Toutes les valeurs doivent être des multiples de 10. Éléments avec une version ultérieure `OpenOrder` valeurs sont d’abord ouvertes.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../extensibility/project-element-visual-studio-templates.md)|Spécifie les fichiers ou répertoires à ajouter au projet.|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Un `string` qui représente le nom ou le chemin d’accès à un fichier dans le fichier .zip du modèle.  
  
## <a name="remarks"></a>Notes  
 `ProjectItem` est un enfant facultatif de `Project`.  
  
 Le `TargetFileName` attribut peut être utilisé pour créer une structure de répertoire différente à partir de la structure de répertoires dans le fichier .zip du modèle. Par exemple, si le fichier `MyFile.vb` existe à la racine du fichier .zip du modèle, mais vous souhaitez que le fichier à placer dans un répertoire nommé `CustomFiles` dans tous les projets créés à partir du modèle, vous utiliseriez le code XML suivant :  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 Le `TargetFileName` attribut peut également être utilisé pour renommer des fichiers qui contiennent des caractères internationaux. Par exemple, un fichier .zip du modèle ne peut pas contenir des noms de fichiers avec des caractères Unicode, donc le fichier doit être renommé avant peuvent être compressée dans un fichier .zip. Le `TargetFileName` attribut peut être utilisé pour définir le nom du fichier vers le nom de fichier Unicode d’origine.  
  
 Le `TargetFileName` attribut peut également être utilisé pour renommer des fichiers avec des paramètres. La procédure suivante explique comment renommer le fichier `MyFile.vb`, qui existe dans le répertoire racine du fichier .zip du modèle, à un nom de fichier basé sur le nom du projet.  
  
### <a name="to-rename-files-with-parameters"></a>Pour renommer des fichiers avec des paramètres  
  
1.  Dans le fichier .vstemplate, utilisez le code XML suivant :  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Ouvrez le fichier projet (.vbproj pour un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projet) dans un éditeur de texte ou [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3.  Recherchez la ligne dans le fichier projet qui ressemble au code XML suivant :  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Remplacez la ligne de code par le code XML suivant :  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Lorsqu’un projet est créé à partir de ce modèle, le nom de fichier doit reposer sur le nom de l’utilisateur a entré dans le **nouveau projet** boîte de dialogue, avec tous les caractères sécurisés et supprimés les espaces. Pour plus d’informations, consultez [paramètres de modèle](../ide/template-parameters.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les métadonnées d’un modèle de projet pour un [!INCLUDE[csprcs](../includes/csprcs-md.md)] application.  
  
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
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Élément ProjectItem (modèles d'élément Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
