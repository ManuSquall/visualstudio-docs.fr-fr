---
title: "L’élément SDKReference (modèles Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2929e53dc3459c1699a0bc09cb235971ba02f90f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sdkreference-element-visual-studio-templates"></a>Élément SDKReference (modèles Visual Studio)
Spécifie que le modèle d’élément utilise une référence SDK.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<VSTemplate>      
    <TemplateContent>          
        <References>              
            <Reference>  
                <SDKReference>SDKname</SDKReference>  
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
|[Référence](../extensibility/reference-element-visual-studio-templates.md)|Spécifie la référence d’assembly à ajouter quand l’élément est ajouté à un projet.|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
## <a name="remarks"></a>Notes  
 Ce texte spécifie la référence SDK à ajouter à un projet quand le modèle d’élément est instancié.  
  
```xml  
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">   
    <TemplateData> . . . </TemplateData>   
    <TemplateContent>   
        <References>   
            <Reference>   
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>  
...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Références, élément (modèles Visual Studio)](../extensibility/references-element-visual-studio-templates.md)   
 [Référence, élément (modèles Visual Studio)](../extensibility/reference-element-visual-studio-templates.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)