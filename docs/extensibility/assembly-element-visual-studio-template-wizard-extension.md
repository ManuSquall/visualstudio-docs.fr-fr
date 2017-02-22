---
title: "Assembly, &#233;l&#233;ment (extension de l’Assistant Mod&#232;le de Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Assembly"
helpviewer_keywords: 
  - "Assembly (élément de l’extension de l’Assistant Modèle Visual Studio)"
  - "élément < assembly > [Visual Studio modèle Assistant Extension]"
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Assembly, &#233;l&#233;ment (extension de l’Assistant Mod&#232;le de Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie le nom ou le nom fort de l’assembly qui implémente le `IWizard` interface.  
  
 \<VSTemplate\>  
\<WizardExtension\>  
\<Assembly\>  
  
## Syntaxe  
  
```  
<Assembly>AssemblyName</Assembly>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contient les éléments d’enregistrement pour la personnalisation de l’Assistant modèle.|  
  
## Valeur texte  
 Une valeur texte est requise.  
  
 Ce texte spécifie l’assembly qui implémente le `IWizard` interface. Nom de l’assembly doit être spécifié comme nom complet de l’assembly. Par exemple, `MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null`.  
  
## Notes  
 `Assembly` est un élément enfant obligatoire de `WizardExtension`.  
  
## Exemple  
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
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Comment : utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)