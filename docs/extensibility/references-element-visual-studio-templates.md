---
title: Fait référence à l’élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ae0ee308af1502a7c07766e790b79e51f692a96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433407"
---
# <a name="references-element-visual-studio-templates"></a>References, élément (modèles Visual Studio)
Regroupe les références d’assembly que le modèle ajoute aux projets.

 \<VSTemplate > \<TemplateContent > \<références >

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
|[Référence](../extensibility/reference-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie la référence d’assembly à ajouter quand l’élément est ajouté à un projet. Il doit y avoir un ou plusieurs `Reference` éléments dans un `References` élément.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Spécifie le contenu du modèle.|

## <a name="remarks"></a>Notes
 `References` est un élément enfant facultatif de `TemplateContent`.

 Le `Reference` et `References` éléments peuvent uniquement être utilisés dans *.vstemplate* fichiers ayant une `Type` valeur d’attribut `Item`.

## <a name="example"></a>Exemple
 L’exemple suivant illustre la `TemplateContent` élément d’un modèle d’élément. Ce code XML ajoute des références à la *System.dll* et *System.Data.dll* assemblys.

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
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)
