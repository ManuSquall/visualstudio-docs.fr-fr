---
title: Description, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Description element [Visual Studio project templates]
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 88b01dfad315d003840bb2eb5f97c7f0022f85e7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906733"
---
# <a name="description-element-visual-studio-templates"></a>Description, élément (modèles Visual Studio)
Spécifie la description du modèle tel qu’il apparaît dans un le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Description >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Description>  
    Template Description  
</Description>  
```  
  
```  
<Description Package="{PackageID}" ID="ResourceID" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Package`|Attribut facultatif, pour les scénarios complexes.<br /><br /> ID un GUID qui spécifie le package Visual Studio d'.|  
|`ID`|Attribut facultatif, pour les scénarios complexes.<br /><br /> Spécifie l’ID de ressource de Visual Studio.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur de texte est obligatoire, sauf si le `Package` et `ID` attributs sont utilisés.  
  
 Le texte fournit une description du modèle.  
  
## <a name="remarks"></a>Notes  
 `Description` est un élément enfant obligatoire de l'élément `TemplateData`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les métadonnées d’un modèle de projet pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application.  
  
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
 [Référence de schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)