---
title: Élément de référence (Modèles de studio visuel) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11d893f6268a69172d27a0f7caee707767abfe89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701624"
---
# <a name="reference-element-visual-studio-templates"></a>Élément de référence (modèles Visual Studio)
Spécifie la référence d’assembly à ajouter quand l’élément est ajouté à un projet.

 \<VSTemplate> \<TemplateContent> \<Références> \<référence>

## <a name="syntax"></a>Syntaxe

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Assemblée](../extensibility/assembly-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie des informations sur une assemblée, que le modèle utilise pour ajouter une référence de cet assemblage aux projets. Il doit `Assembly` y avoir `Reference` un élément dans chaque élément.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Informations de référence](../extensibility/references-element-visual-studio-templates.md)|Regroupe les références d’assemblage que le modèle ajoute aux projets.|

## <a name="remarks"></a>Notes
 `Reference` est un élément enfant obligatoire de `References`.

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
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
