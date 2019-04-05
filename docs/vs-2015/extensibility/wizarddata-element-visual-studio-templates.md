---
title: WizardData, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d7cd59266a69140ba2ea5a7fd1d1b0b0c72f14c2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952296"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData, élément (modèles Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie le code XML personnalisé  
  
 \<VSTemplate>  
 \<WizardData>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<WizardData>  
    <!-- XML to pass to the custom wizard extension -->  
    ...  
</WizardData>  
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Élément requis.<br /><br /> Contient toutes les métadonnées pour le modèle de projet, un modèle d’élément ou un starter kit.|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est facultative.  
  
 Ce texte spécifie la partie XML personnalisée à passer à l’extension d’Assistant personnalisée spécifiée dans le [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) élément.  
  
## <a name="remarks"></a>Notes  
 Tout code XML peut être spécifiée dans cet élément. Le code XML sera passé comme un paramètre à l’extension d’Assistant personnalisée, ce qui permet l’extension à utiliser le contenu de cet élément. Aucune validation n’est effectuée sur ces données.  
  
 Le contenu de la `WizardData` élément sont passés, inchangé, en tant que paramètre à l’intérieur du dictionnaire de chaînes de paramètres dans le `IWizard.RunStarted` (méthode). Le paramètre est nommé $WizardData$.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre les métadonnées pour le modèle de projet standard pour une [!INCLUDE[csprcs](../includes/csprcs-md.md)] application de Windows.  
  
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
    <WizardData>  
        <!-- XML to pass to the custom wizard extension -->  
    </WizardData>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [WizardExtension, élément (modèles Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)   
 [Guide pratique pour Utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)
