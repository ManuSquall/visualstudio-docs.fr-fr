---
title: SupportsLanguageDropDown, élément (modèles Visual Studio)
titleSuffix: ''
description: En savoir plus sur l’élément SupportsLanguageDropDown et sur la façon dont il spécifie si le modèle d’élément Web est identique pour plusieurs langues, et si l’option de langue est activée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67bf92c8c447faac2969bde3f208823158663712
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056075"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown, élément (modèles Visual Studio)

Spécifie si le modèle d’élément Web est identique pour plusieurs langues et si l’option de **langue** est activée dans la boîte de dialogue **Ajouter un nouvel élément** .

 \<VSTemplate> \<TemplateData>
 \<SupportsLanguageDropDown>

## <a name="syntax"></a>Syntaxe

```xml
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte

 Une valeur texte est requise.

 Le texte doit être `true` ou `false` , indiquant si l’option de **langue** est disponible ou non dans la boîte de dialogue **Ajouter un nouvel élément** .

## <a name="remarks"></a>Notes

 `SupportsLanguageDropDown` est un élément facultatif. La valeur par défaut est `false`.

 L' `SupportsLanguageDropDown` élément est uniquement disponible pour les modèles d’élément Web.

 Si la valeur de cet élément est définie sur `true` , le modèle d’élément est identique pour tous les langages de programmation et l’option de **langue** est activée dans la boîte de dialogue **Ajouter un nouvel élément** . Cette option vous permet de choisir le langage de programmation du nouvel élément que vous souhaitez créer à partir du modèle.

## <a name="example"></a>Exemple

 L’exemple suivant spécifie l’affichage de l’option de liste déroulante **langue** .

```xml
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
