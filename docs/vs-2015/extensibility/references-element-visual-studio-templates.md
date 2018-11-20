---
title: Fait référence à l’élément (modèles Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5e3e0df8583e48dd6a3f7604f4fa72b2803779b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795651"
---
# <a name="references-element-visual-studio-templates"></a>References, élément (modèles Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regroupe les références d’assembly que le modèle ajoute aux projets.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Références >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Référence](../extensibility/reference-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie la référence d’assembly à ajouter quand l’élément est ajouté à un projet. Il doit y avoir un ou plusieurs `Reference` éléments dans un `References` élément.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Spécifie le contenu du modèle.|  
  
## <a name="remarks"></a>Notes  
 `References` est un élément enfant facultatif de `TemplateContent`.  
  
 Le `Reference` et `References` éléments peuvent uniquement être utilisés dans les fichiers .vstemplate ayant un `Type` valeur d’attribut `Item`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la `TemplateContent` élément d’un modèle d’élément. Ce code XML ajoute des références aux assemblys System.dll et System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)

