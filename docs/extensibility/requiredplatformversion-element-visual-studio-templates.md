---
title: "&#201;l&#233;ment RequiredPlatformVersion (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# &#201;l&#233;ment RequiredPlatformVersion (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie la version minimale du système d’exploitation que le modèle de projet a besoin pour fonctionner correctement. Cet élément est utilisé pour des modèles de projet qui créent des [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] applications.  
  
 Le `RequiredPlatformVersion` la valeur est comparée directement avec la version du système d’exploitation. Si la `RequiredPlatformVersion` est supérieure à la version du système d’exploitation, le modèle n’apparaît pas dans le **Nouveau projet** boîte de dialogue. Pour spécifier un modèle pour [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou version ultérieure, définissez `RequiredPlatformVersion` à 6.2.0. Pour spécifier un modèle pour [!INCLUDE[win81](../debugger/includes/win81_md.md)] ou supérieure, définie RequiredPlatformVersion à 6.3.0.  
  
 Modèles qui spécifient `RequiredPlatformVersion`\= 8 sont compatibles avec le client précédent [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] modèles.  
  
 VSTemplate  
TemplateData  
…..TargetPlatformName  
RequiredPlatformVersion  
  
## Syntaxe  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## Attributs et éléments  
 Aucune.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Spécifie la plateforme ciblée par le modèle de projet.|  
  
## Valeur texte  
 Une valeur texte est requise.  
  
## Notes  
 Ce texte spécifie la version du système d’exploitation minimal requise par le modèle.  
  
## Exemple  
 Cet exemple spécifie que le modèle de projet cible [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou version ultérieure.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Voir aussi  
 [Élément TargetPlatformName \(modèles Visual Studio\)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)