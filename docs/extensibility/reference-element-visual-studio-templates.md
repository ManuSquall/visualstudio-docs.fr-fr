---
title: Reference, élément (modèles Visual Studio) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701624"
---
# <a name="reference-element-visual-studio-templates"></a>Reference, élément (modèles Visual Studio)
Spécifie la référence d’assembly à ajouter quand l’élément est ajouté à un projet.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>

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
|[Chargeur](../extensibility/assembly-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie des informations sur un assembly, que le modèle utilise pour ajouter une référence de cet assembly aux projets. Il doit y avoir un `Assembly` élément dans chaque `Reference` élément.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Informations de référence](../extensibility/references-element-visual-studio-templates.md)|Regroupe les références d’assembly que le modèle ajoute aux projets.|

## <a name="remarks"></a>Notes
 `Reference` est un élément enfant obligatoire de `References`.

 Les `Reference` `References` éléments et peuvent uniquement être utilisés dans les fichiers *. vstemplate* qui ont une `Type` valeur d’attribut de `Item` .

## <a name="example"></a>Exemple
 L’exemple suivant illustre l' `TemplateContent` élément d’un modèle d’élément. Ce code XML ajoute des références aux assemblys *System.dll* et *System.Data.dll* .

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
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
