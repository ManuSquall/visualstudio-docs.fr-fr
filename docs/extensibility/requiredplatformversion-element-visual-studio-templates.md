---
title: L’élément RequiredPlatformVersion (modèles Visual Studio) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35a8dc6fa57dbe88ce1e30e9be58105f28fe5641
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Élément RequiredPlatformVersion (modèles Visual Studio)
Spécifie la version minimale du système d’exploitation que le modèle de projet a besoin pour fonctionner correctement. Cet élément est utilisé pour des modèles de projet qui créent [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] applications.  
  
 Le `RequiredPlatformVersion` valeur est comparée directement avec la version du système d’exploitation. Si le `RequiredPlatformVersion` est supérieure à la version du système d’exploitation, le modèle n’apparaît pas dans le **nouveau projet** boîte de dialogue. Pour spécifier un modèle pour [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou supérieur, définissez `RequiredPlatformVersion` à 6.2.0. Pour spécifier un modèle pour [!INCLUDE[win81](../debugger/includes/win81_md.md)] ou supérieure, définie RequiredPlatformVersion à 6.3.0.  
  
 Les modèles qui spécifient `RequiredPlatformVersion`= 8 sont compatibles avec le client précédente [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] modèles.  
  
 VSTemplate  
TemplateData  
..... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Aucun.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Spécifie la plateforme ciblée par le modèle de projet.|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
## <a name="remarks"></a>Notes  
 Ce texte spécifie la version minimale du système d’exploitation requise par le modèle.  
  
## <a name="example"></a>Exemple  
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
  
## <a name="see-also"></a>Voir aussi  
 [Élément TargetPlatformName (modèles Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)