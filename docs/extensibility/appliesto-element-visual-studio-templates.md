---
title: AppliesTo, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39b5ee1e3cad0b4d8ddbe0fc2dfa1c2d478ec063
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740071"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo, élément (modèles Visual Studio)

Spécifie une expression facultative qui correspond à une ou plusieurs fonctionnalités (consultez <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher> ). Les fonctionnalités sont exposées par types de projets via la hiérarchie en tant que propriété [__VSHPROPID5. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). De cette manière, le modèle peut être partagé par plusieurs types de projets ayant des capacités applicables communes.

Cet élément est facultatif. Il peut y avoir au maximum une instance dans un fichier modèle. Cet élément permet uniquement à un modèle d'élément d'être déclaré comme applicable, en fonction des fonctionnalités du projet actif sélectionné. Il ne peut pas être utilisé pour rendre un modèle d'élément non applicable. Si `AppliesTo` est absent ou si l'expression ne permet pas de déclarer correctement, alors `TemplateID` ou `TemplateGroupID` est utilisé pour rendre le modèle applicable, comme avec les versions antérieures du produit.

Introduit pour la première fois dans Visual Studio 2013 Update 2. Pour référencer la version appropriée, consultez [référencement des assemblys fournis dans le kit de développement logiciel (SDK) Visual Studio 2013 Update 2](/previous-versions/dn632168(v=vs.120)).

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Syntaxe

```xml
<AppliesTo>Capability1</AppliesTo>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Définit la catégorie du modèle.|

## <a name="text-value"></a>Valeur texte

Une valeur texte est requise. Ce texte spécifie les fonctionnalités du projet.

La syntaxe d'expression valide est définie comme suit :

- Expression de fonctionnalité, telle que « (VisualC &#124; CSharp) + (MSTest &#124; NUnit) ».

- « &#124; » est l’opérateur OR.

- Les caractères « & » et « + » sont à la fois des opérateurs et.

- Le caractère « ! » est l'opérateur NOT.

- Les parenthèses forcent l'ordre de priorité de l'évaluation.

- Une expression null ou vide est évaluée comme une correspondance.

- Les fonctionnalités du projet peuvent être n’importe quel caractère, à l’exception des caractères réservés suivants : "' ' :;, +-*/ \\ ! ~&#124;&% $ @ ^ () = {} [] <> ? \t\b\n\r

## <a name="example"></a>Exemple

L'exemple suivant indique trois modèles différents. `Template1` s’applique soit à tous les types de projets C#, soit à tout autre type de projet qui prend en charge la `WindowsAppContainer` fonctionnalité. `Template2` s’applique à tous les projets C# de tout type. `Template3` s'applique aux projets C# qui ne sont pas des projets `WindowsAppContainer`.

```xml
<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 2 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>
    </TemplateData>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
