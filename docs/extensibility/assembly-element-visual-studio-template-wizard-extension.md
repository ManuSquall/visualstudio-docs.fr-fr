---
title: Assembly, élément (Extension de l’Assistant modèle Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio Template Wizard Extension]
- <Assembly> element [Visual Studio Template Wizard Extension]
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55cbc596824e0a02398ee1ad0ff420db0746089a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010247"
---
# <a name="assembly-element-visual-studio-template-wizard-extension"></a>Assembly, élément (extension de l’Assistant modèle Visual Studio)
Spécifie le nom ou le nom fort de l’assembly qui implémente le `IWizard` interface.  
  
 \<VSTemplate>  
\<WizardExtension>  
\<Assembly>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Assembly>AssemblyName</Assembly>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contient les éléments de l’inscription pour la personnalisation de l’Assistant modèle.|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Ce texte spécifie l’assembly qui implémente le `IWizard` interface. Ce nom de l’assembly doit être spécifié comme un nom complet de l’assembly. Par exemple, `MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null`.  
  
## <a name="remarks"></a>Notes  
 `Assembly` est un élément enfant obligatoire de `WizardExtension`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre les métadonnées pour le modèle de projet standard pour une [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application de Windows.  
  
```xml
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)
- [Guide pratique pour Utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)