---
title: Élément d’assemblage (Modèles de studio visuel) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740033"
---
# <a name="assembly-element-visual-studio-templates"></a>Élément d’assemblage (modèles Visual Studio)
Spécifie des informations sur une assemblée, que le modèle utilise pour ajouter une référence de cet assemblage aux projets.

 \<VSTemplate> \<TemplateContent> \<Références> \<Référence> \<Assemblée>

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

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Ce texte spécifie l’assemblage à ajouter à un projet lorsque le modèle d’élément est instantané. Ce nom d’assemblage doit être spécifié de l’une des façons suivantes :

- Comme nom d’assemblée complète. Par exemple :

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Comme simple référence de texte. Par exemple :

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Notes
 `Assembly` est un élément enfant obligatoire de `Reference`.

 Le `Reference` `References,` , `Assembly` et les éléments ne peuvent être utilisés `Type` que dans `Item`les fichiers *.vstemplate* qui ont une valeur d’attribut de .

## <a name="example"></a>Exemple
 L’exemple suivant `TemplateContent` illustre l’élément d’un modèle d’élément. Ce XML ajoute des références aux assemblages *System.dll* et *System.Data.dll.*

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
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
