---
title: TemplateData, élément (modèles Visual Studio) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbf5b4c26b46c0be6038651a41c751afc39e4da5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData, élément (modèles Visual Studio)
Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .  
  
 \<VSTemplate >  
 \<TemplateData >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Nom](../extensibility/name-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie le nom du modèle tel qu’il apparaît, que ce soit le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|  
|[Description](../extensibility/description-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie la description du modèle tel qu’il apparaît, que ce soit le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|  
|[Icône](../extensibility/icon-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie le chemin d’accès et le nom de fichier du fichier image qui sert d’icône qui s’affiche, que ce soit le **nouveau projet** ou le **ajouter un nouvel élément** boîte de dialogue, pour le modèle.|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|Élément requis.<br /><br /> Catégorie du modèle de projet afin qu’il apparaisse sous le groupe spécifié dans le **nouveau projet** boîte de dialogue.|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Classe le modèle de projet afin qu’il apparaisse dans la sous-catégorie spécifiée dans le **nouveau projet** boîte de dialogue.|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie l’ID de modèle.|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie l’ID de groupe de modèles.|  
|[Ordre de tri](../extensibility/sortorder-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie une valeur qui est utilisée pour organiser le modèle, parmi d’autres modèles dans la même catégorie, telle qu’elle apparaît, que ce soit le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie si un dossier conteneur est créé lors de l’instanciation du projet.|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie le nom que le système de projet Visual Studio génère pour le projet ou l’élément lors de sa création.|  
|[ProvideDefaultName la valeur](../extensibility/providedefaultname-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie si le système de projet Visual Studio génère le nom par défaut pour un projet ou un élément lors de sa création.|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie si le projet peut être créé comme un projet temporaire.|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie si le **Parcourir** bouton n’est disponible dans le **nouveau projet** boîte de dialogue, afin que les utilisateurs peuvent facilement modifier le répertoire par défaut dans lequel un nouveau projet est enregistré.|  
|[Masqué](../extensibility/hidden-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie si le modèle s’affiche, que ce soit le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie le nombre de catégories parentes qui afficheront le modèle dans le **nouveau projet** boîte de dialogue.|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|Élément facultatif.|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|Élément facultatif.<br /><br /> Spécifie si le **emplacement** zone de texte dans le **nouveau projet** boîte de dialogue est activée, désactivée ou masquée pour le modèle de projet.|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Utilisez cet élément si le modèle prend uniquement en charge une version minimale spécifique et les versions ultérieures éventuelles du .NET Framework.|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie si le modèle prend en charge une page maître pour les projets web.|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie si le modèle prend en charge la séparation de code, ou le modèle de page code-behind, pour les projets web.|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie que le modèle est identique pour plusieurs langages et si le **langage** option est disponible à partir de la **nouveau projet** boîte de dialogue.|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie la plateforme ciblée par le modèle de projet. Cet élément spécifie qu’un modèle de projet permet de créer [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] applications.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Élément requis.<br /><br /> Contient toutes les métadonnées pour le modèle de projet, un modèle d’élément ou un starter kit.|  
  
## <a name="remarks"></a>Notes  
 `TemplateData` est un élément requis.  
  
 Si vous n’incluez pas un élément facultatif, la valeur par défaut de cet élément est utilisée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affiche les métadonnées d’un modèle de projet pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application.  
  
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
            <ProjectItem>Form1.cs<ProjectItem>  
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