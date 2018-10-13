---
title: Élément MaxFrameworkVersion (modèles Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94b12af3d2b0c455ae321b3329b1f90d2ab35fb2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276820"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Élément MaxFrameworkVersion (modèles Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie la version maximale du .NET Framework qui est requis par le modèle. Il détermine si le modèle est affiché dans le **modèles** section de la **ajouter un nouveau projet** boîte de dialogue, selon la valeur qui est sélectionnée dans le **VersionduFrameworkcible** zone de la **ajouter un nouveau projet** boîte de dialogue.  
  
 \<VSTemplate >  
 \<MaxFrameworkVersion >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il est affiché dans un le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Le texte doit être le numéro de version le plus élevé du .NET Framework qui est autorisé par le modèle.  
  
## <a name="remarks"></a>Notes  
 `MaxFrameworkVersion` est un élément facultatif. L’élément dans le `TemplateData` section du fichier .vstemplate agit comme un filtre pour le **modèles** section de la **ajouter un nouveau projet** boîte de dialogue. Uniquement les modèles dont les exigences de .NET Framework sont moins de `MaxFrameworkVersion` valeurs d’élément seront affiche, selon la valeur qui est sélectionnée dans le **Version du Framework cible** boîte de le **ajouter un nouveau projet**boîte de dialogue. Le `MaxFrameworkVersion` élément doit être omis, sauf si elle est nécessaire, pour autant entraîner par inadvertance des modèles de s’afficher lorsqu’ils sont utilisés avec des versions plus récentes du .NET Framework.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre les métadonnées d’une norme [!INCLUDE[csprcs](../includes/csprcs-md.md)] modèle de classe.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Dans cet exemple, la version maximale du .NET Framework qui est requis par le modèle, représenté par `MaxFrameworkVersion`, est 3.5. Le modèle ci-dessus s’affichera uniquement lorsque vous sélectionnez 3.0 ou 3.5 dans le **Version du Framework cible** zone le **ajouter un nouveau projet** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)

