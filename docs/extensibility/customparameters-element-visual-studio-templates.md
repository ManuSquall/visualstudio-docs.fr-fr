---
title: "CustomParameters, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters"
helpviewer_keywords: 
  - "CustomParameters (élément de modèles de projet Visual Studio)"
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# CustomParameters, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Regroupe les paramètres personnalisés qui doivent être passés à l’Assistant modèle lorsque les remplacements de paramètres.  
  
## Syntaxe  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Contient un nom de paramètre personnalisé et une valeur à utiliser lorsqu’un projet ou un élément est créé à partir du modèle. Un élément `CustomParameter` peut ne contenir aucun élément `CustomParameters` ou en contenir plusieurs.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Spécifie le contenu du modèle.|  
  
## Notes  
  
## Exemple  
 L’exemple suivant montre comment utiliser plusieurs paramètres personnalisés dans un modèle. Création d’un projet ou un élément à partir d’un modèle avec les paramètres personnalisés suivants, toutes les instances de `$color1$` et `$color2$` dans le modèle, les fichiers sont remplacés par `Red` et `Blue`, respectivement.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## Voir aussi  
 [CustomParameter, élément \(modèles Visual Studio\)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)