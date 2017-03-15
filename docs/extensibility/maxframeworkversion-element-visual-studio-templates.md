---
title: "&#201;l&#233;ment MaxFrameworkVersion (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<MaxFrameworkVersion> (élément de modèles Visual Studio)"
  - "Élément MaxFrameworkVersion (modèles Visual Studio)"
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# &#201;l&#233;ment MaxFrameworkVersion (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie la version maximale de .NET Framework qui est requise par le modèle.  Il détermine si le modèle doit s'afficher dans la section **Modèles** de la boîte de dialogue **Ajouter un nouveau projet**, selon la valeur entrée dans la zone **Version du Framework cible** de la boîte de dialogue **Ajouter un nouveau projet**.  
  
## Syntaxe  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle dans une catégorie et définit la façon dont il s'affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.|  
  
## Valeur texte  
 Une valeur texte est requise.  
  
 Le texte doit avoir le numéro de la version la plus récente de .NET Framework qui soit autorisée par le modèle.  
  
## Notes  
 `MaxFrameworkVersion` est un élément facultatif.  L'élément dans la section `TemplateData` du fichier .vstemplate agit comme filtre pour la section **Modèles** de la boîte de dialogue **Ajouter un nouveau projet**.  Seuls les modèles dont les spécifications .NET Framework sont inférieures aux valeurs d'élément `MaxFrameworkVersion` sont affichées en fonction de la valeur sélectionnée dans la zone **Version du Framework cible** de la boîte de dialogue **Ajouter un nouveau projet**.  L'élément `MaxFrameworkVersion` doit être omis à moins qu'il ne soit requis, afin de ne pas causer par inadvertance que les modèles soient affichés lorsqu'ils sont utilisés avec les versions plus récentes de .NET Framework.  
  
## Exemple  
 L'exemple suivant illustre les métadonnées d'un modèle de classe [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] standard.  
  
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
  
 Dans cet exemple, la version maximale de .NET Framework qui est requise par le modèle, représenté par `MaxFrameworkVersion`, est 3.5.  Le modèle ci\-dessus sera affiché uniquement lorsque vous entrez 3,0 ou 3,5 dans la zone **Version cible du .NET Framework** dans la boîte de dialogue **Ajouter un nouveau projet**.  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)