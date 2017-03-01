---
title: "WizardExtension, élément (modèles Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d23e6d14cd7118838bbe6e143bebd073171c73de
ms.lasthandoff: 02/22/2017

---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension, élément (modèles Visual Studio)
Contient les éléments d’enregistrement pour la personnalisation de l’Assistant modèle.  
  
 \<VSTemplate >  
 ...  
 \<WizardExtension >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<WizardExtension>  
    <Assembly>... </Assembly>  
    <FullClassName>... </FullClassName>  
</WizardExtension>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|Élément requis.<br /><br /> Spécifie le nom ou le nom fort d’un assembly qui s’affiche dans le global assembly cache. Il doit y avoir au moins un `Assembly` élément dans un `WizardExtension` élément.|  
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|Élément requis.<br /><br /> Le nom qualifié complet de la classe qui implémente le `IWizard` interface. Il doit y avoir au moins un `FullClassName` élément dans un `WizardExtension` élément.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Contient toutes les métadonnées pour le modèle de projet, un modèle d’élément ou un kit de démarrage.|  
  
## <a name="remarks"></a>Notes  
 `WizardExtension` est un élément enfant facultatif de `VSTemplate`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre les métadonnées du modèle de projet standard pour une [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application Windows.  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de projet et modèles d’élément](../ide/creating-project-and-item-templates.md)   
 [Comment : utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)
