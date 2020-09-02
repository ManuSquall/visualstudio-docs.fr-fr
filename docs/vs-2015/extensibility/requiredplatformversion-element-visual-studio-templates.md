---
title: Élément RequiredPlatformVersion (modèles Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e5ba8cfef6674b5603cf03c73619f686338af3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159291"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Élément RequiredPlatformVersion (modèles Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie la version minimale du système d’exploitation requise par le modèle de projet pour fonctionner correctement. Cet élément est utilisé pour les modèles de projet qui créent des [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] applications.  
  
 La `RequiredPlatformVersion` valeur est comparée directement à la version du système d’exploitation. Si le `RequiredPlatformVersion` est supérieur à la version du système d’exploitation, le modèle n’apparaît pas dans la boîte de dialogue **nouveau projet** . Pour spécifier un modèle pour [!INCLUDE[win8](../includes/win8-md.md)] ou version ultérieure, définissez `RequiredPlatformVersion` sur 6.2.0. Pour spécifier un modèle pour [!INCLUDE[win81](../includes/win81-md.md)] ou version ultérieure, définissez RequiredPlatformVersion sur 6.3.0.  
  
 Les modèles qui spécifient `RequiredPlatformVersion` = 8 sont compatibles avec les modèles de client précédents [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] .  
  
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
 Cet exemple spécifie que le modèle de projet cible [!INCLUDE[win8](../includes/win8-md.md)] ou version ultérieure.  
  
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
