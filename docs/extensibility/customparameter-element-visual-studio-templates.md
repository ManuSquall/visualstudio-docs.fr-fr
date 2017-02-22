---
title: "CustomParameter, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter"
helpviewer_keywords: 
  - "CustomParameters (élément de modèles de projet Visual Studio)"
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# CustomParameter, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient le nom et la valeur d'un paramètre personnalisé à utiliser lorsque vous créez un projet ou un élément à partir du modèle.  
  
## Syntaxe  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Requis.  Nom du paramètre.  Les paramètres ont le format $*nom*$.|  
|`Value`|Requis.  Valeur de remplacement du paramètre.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Groupe les paramètres personnalisés à passer à l'Assistant du modèle lors des remplacements de paramètres.|  
  
## Notes  
 Lorsqu'un modèle contient des éléments `CustomParameter`, chaque instance de l'attribut `Name` est remplacée par l'attribut `Value` dans les fichiers du projet ou de l'élément créé.  
  
## Exemple  
 L'exemple suivant indique comment utiliser plusieurs paramètres personnalisés dans un modèle.  Lorsqu'un projet ou l'élément est créé à partir d'un modèle avec les paramètres personnalisés suivants, toutes les instances de `$color1$` et `$color2$` dans les fichiers modèles sont remplacées par `Red` et `Blue`, respectivement.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## Voir aussi  
 [CustomParameters, élément \(modèles Visual Studio\)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)