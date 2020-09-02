---
title: Élément MaxFrameworkVersion (modèles Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194330"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Élément MaxFrameworkVersion (modèles Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie la version maximale du .NET Framework requis par le modèle. Elle détermine si le modèle est affiché dans la section **modèles** de la boîte de dialogue **Ajouter un nouveau projet** , en fonction de la valeur sélectionnée dans la zone **version du Framework cible** de la boîte de dialogue **Ajouter un nouveau projet** .  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle et définit son mode d’affichage dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** .|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Le texte doit être le numéro de version le plus élevé du .NET Framework qui est autorisé par le modèle.  
  
## <a name="remarks"></a>Notes  
 `MaxFrameworkVersion` est un élément facultatif. L’élément dans la `TemplateData` section du fichier. vstemplate agit comme un filtre pour la section **modèles** de la boîte de dialogue **Ajouter un nouveau projet** . Seuls les modèles dont les exigences de .NET Framework sont inférieures à celles `MaxFrameworkVersion` des éléments seront affichés, en fonction de la valeur sélectionnée dans la zone **version du Framework cible** de la boîte de dialogue **Ajouter un nouveau projet** . L' `MaxFrameworkVersion` élément doit être omis, sauf s’il est requis, afin de ne pas empêcher par inadvertance les modèles d’être affichés lorsqu’ils sont utilisés avec des versions plus récentes du .NET Framework.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre les métadonnées pour un [!INCLUDE[csprcs](../includes/csprcs-md.md)] modèle de classe standard.  
  
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
  
 Dans cet exemple, la version maximale du .NET Framework requis par le modèle, représenté par `MaxFrameworkVersion` , est 3,5. Le modèle ci-dessus s’affiche uniquement lorsque vous sélectionnez 3,0 ou 3,5 dans la zone **version du Framework cible** de la boîte de dialogue **Ajouter un nouveau projet** .  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
