---
title: Élément RequiredPlatformVersion (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f77b14903ccf5569755cf7116a1365d5ba8487c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850386"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Élément RequiredPlatformVersion (modèles Visual Studio)
Spécifie la version minimale du système d’exploitation que le modèle de projet a besoin pour fonctionner correctement. Cet élément est utilisé pour des modèles de projet qui créent des [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] applications.  
  
 Le `RequiredPlatformVersion` valeur est comparée directement à la version du système d’exploitation. Si le `RequiredPlatformVersion` est supérieure à la version de système d’exploitation, le modèle n’apparaît pas dans le **nouveau projet** boîte de dialogue. Pour spécifier un modèle pour [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou version ultérieure, définissez `RequiredPlatformVersion` à 6.2.0. Pour spécifier un modèle pour [!INCLUDE[win81](../debugger/includes/win81_md.md)] ou version ultérieure, définissez `RequiredPlatformVersion` vers la version 6.3.0.  
  
 Les modèles qui spécifient `RequiredPlatformVersion`= 8 sont compatibles avec le client précédent [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] modèles.  
  
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
 [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)