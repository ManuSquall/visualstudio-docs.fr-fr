---
title: "R&#233;f&#233;rence du sch&#233;ma de mod&#232;le Visual&#160;Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers .vstemplate"
  - "modèles Visual Studio, schéma"
  - "fichiers VSTEMPLATE"
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# R&#233;f&#233;rence du sch&#233;ma de mod&#232;le Visual&#160;Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section contient des informations sur les éléments XML dans des fichiers .vstemplate, qui stockent les métadonnées des modèles de projet, d'élément et des Starter Kits.  
  
 Vous pouvez utiliser vstemplate.xsd pour valider des fichiers .vstemplate personnalisés.  Ce fichier est disponible dans ..\\*Visual Studio installation folder*\\Xml\\Schemas\\1033\\vstemplate.xsd.  
  
|Élément|Éléments enfants|Attributs|  
|-------------|----------------------|---------------|  
|[AppliesTo](../extensibility/appliesto-element-visual-studio-templates.md)|Aucune|Aucune|  
|[Assembly \(modèle\)](../extensibility/assembly-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Assembly \(Extension Assistant\)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|\-\-|\-\-|  
|[BuildProjectOnload](../extensibility/buildprojectonload-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|\-\-|\-\-|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CustomDataSignature](../extensibility/customdatasignature-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|\-\-|Nom<br /><br /> Valeur|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|\-\-|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Description](../extensibility/description-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[EnableEditOfLocationField](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|\-\-|\-\-|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Dossier](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> Dossier|Nom|  
||\[deprecated\]|\-\-|  
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|\-\-|\-\-|  
|[Hidden](../extensibility/hidden-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Icône](../extensibility/icon-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|\-\-|\-\-|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|\-\-|\-\-|  
|[MaxFrameworkVersion](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Nom](../extensibility/name-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|\-\-|\-\-|  
|[PreviewImage](../extensibility/previewimage-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Dossier<br /><br /> ProjectItem|Fichier<br /><br /> TargetFileName<br /><br /> ReplaceParameters|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|\-\-|  
|[ProjectItem \(Modèles d'élément\)](../extensibility/projectitem-element-visual-studio-item-templates.md)|\-\-|SubType<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|  
|[ProjectItem \(modèles de projet\)](../extensibility/projectitem-element-visual-studio-project-templates.md)|\-\-|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|\-\-|\-\-|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|\-\-|NomProjet|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|\-\-|\-\-|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|\-\-|\-\-|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Référence](../extensibility/reference-element-visual-studio-templates.md)|Assembly|\-\-|  
|[Références](../extensibility/references-element-visual-studio-templates.md)|Référence|\-\-|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|\-\-|\-\-|  
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|\-\-|Version|  
|[SDKReference](72c8b352-0b7a-42b3-ba5d-2a2d1e90c3)|\-\-|Package|  
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|\-\-|\-\-|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|Nom|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|\-\-|\-\-|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|\-\-|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> Project<br /><br /> Références<br /><br /> ProjectItem<br /><br /> CustomParameters|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Nom<br /><br /> Description<br /><br /> Icône<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> Hidden<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|\-\-|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|\-\-|\-\-|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|\-\-|\-\-|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|Type<br /><br /> Version|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|\-\-|Nom|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Assembly<br /><br /> FullClassName|\-\-|  
  
## Voir aussi  
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Comment : créer des Starter Kits](../ide/how-to-create-starter-kits.md)