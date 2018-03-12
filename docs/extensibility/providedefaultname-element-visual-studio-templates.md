---
title: "ProvideDefaultName, élément (modèles Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 48dbc92687a813dcd2a99659b9c2a8cc26129c79
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName, élément (modèles Visual Studio)
Spécifie si le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] système de projet génère un nom par défaut pour le modèle dans le **ajouter un nouvel élément** ou **nouveau projet** boîte de dialogue.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProvideDefaultName la valeur >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Le texte doit être `true` ou `false`, indiquant s’il faut ou non générer un nom par défaut pour le modèle dans le **ajouter un nouvel élément** ou **nouveau projet** boîte de dialogue.  
  
## <a name="remarks"></a>Notes  
 `ProvideDefaultName` est un élément facultatif. La valeur par défaut est `true`.  
  
 Si le `ProvideDefaultName` élément est `false`, le **nom** zones de la **ajouter un nouvel élément** et **nouveau projet** boîtes de dialogue contiennent la valeur `<Enter_name>`.  
  
 Utilisez le [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) élément pour spécifier le nom par défaut du projet ou d’élément dans le **ajouter un nouvel élément** et **nouveau projet** boîtes de dialogue.  
  
## <a name="example"></a>Exemple  
 Le code suivant exemple définit le `ProvideDefaultName` élément `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)