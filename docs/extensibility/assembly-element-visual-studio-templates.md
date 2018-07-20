---
title: Assembly, élément (modèles Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 195faf23ecb2fca019b4948b3150ab6f9c00f5ec
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155462"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly, élément (modèles Visual Studio)
Spécifie les informations relatives à un assembly, le modèle utilise pour ajouter une référence de cet assembly aux projets.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Références >  
 \<Référence >  
 \<Assembly >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Assembly> AssemblyName </Assembly>  
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
  
## <a name="text-value"></a>Valeur de texte  
 Une valeur texte est requise.  
  
 Ce texte spécifie l’assembly à ajouter à un projet lorsque le modèle d’élément est instancié. Ce nom d’assembly doit être spécifié dans une des manières suivantes :  
  
-   En tant que nom complet de l’assembly. Exemple :  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   En tant que référence de texte simple. Exemple :  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Notes  
 `Assembly` est un élément enfant obligatoire de `Reference`.  
  
 Le `Reference`, `References,` et `Assembly` éléments peuvent uniquement être utilisés dans *.vstemplate* fichiers ayant une `Type` valeur d’attribut `Item`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la `TemplateContent` élément d’un modèle d’élément. Ce code XML ajoute des références à la *System.dll* et *System.Data.dll* assemblys.  
  
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
 [Référence de schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)