---
title: Élément de référence (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef31c5e7550ec7c6e4570d156d364afcf4ad6819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701615"
---
# <a name="references-element-visual-studio-templates"></a>Élément de référence (modèles Visual Studio)
Regroupe les références d’assemblage que le modèle ajoute aux projets.

 \<VSTemplate> \<TemplateContent> \<Références>

## <a name="syntax"></a>Syntaxe

```xml
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
|[Référence](../extensibility/reference-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie la référence d’assembly à ajouter quand l’élément est ajouté à un projet. Il doit y `Reference` avoir un `References` ou plusieurs éléments dans un élément.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Spécifie le contenu du modèle.|

## <a name="remarks"></a>Notes
 `References` est un élément enfant facultatif de `TemplateContent`.

 Les `Reference` `References` éléments et les éléments ne peuvent être utilisés `Type` que `Item`dans des fichiers *.vstemplate* qui ont une valeur d’attribut de .

## <a name="example"></a>Exemple
 L’exemple suivant `TemplateContent` illustre l’élément d’un modèle d’élément. Ce XML ajoute des références aux assemblages *System.dll* et *System.Data.dll.*

```xml
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
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
