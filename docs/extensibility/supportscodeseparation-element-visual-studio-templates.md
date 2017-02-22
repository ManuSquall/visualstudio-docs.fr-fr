---
title: "SupportsCodeSeparation, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation"
helpviewer_keywords: 
  - "<SupportsCodeSeparation> (élément de modèles Visual Studio)"
  - "SupportsCodeSeparation (élément de modèles Visual Studio)"
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SupportsCodeSeparation, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie si la case à cocher **Placer le code dans un fichier distinct** est activée dans la boîte de dialogue **Ajouter un nouvel élément**.  
  
## Syntaxe  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle dans une catégorie et définit la façon dont il s'affiche dans la boîte de dialogue **Nouveau projet** ou **Nouvel élément**.|  
  
## Valeur texte  
 Une valeur texte est requise.  
  
 Le texte doit avoir la valeur `true` ou `false`, qui indique si oui ou non la case à cocher **Placer le code dans un fichier distinct** sera activée dans la boîte de dialogue **Ajouter un nouvel élément**.  
  
## Notes  
 `SupportsCodeSeparation` est un élément facultatif.  La valeur par défaut est `false`.  
  
 L'élément `SupportsCodeSeparation` n'est disponible que pour les modèles d'élément Web.  
  
 La séparation de code, ou le modèle de page code\-behind, vous permet de conserver le balisage dans un fichier et le code de programmation dans un autre.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et d'autres langages .NET utilisent ce modèle.  
  
## Exemple  
 L'exemple suivant demande à afficher l'option **Placer le code dans un fichier distinct**.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)