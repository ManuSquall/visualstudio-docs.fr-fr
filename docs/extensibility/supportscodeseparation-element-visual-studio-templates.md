---
title: SupportsCodeSeparation, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4a9e7ba92b9f48cf22999d53ecf6c7b7d832ab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316949"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation, élément (modèles Visual Studio)
Spécifie ou non le **placer le code dans un fichier distinct** case à cocher est activée dans le **ajouter un nouvel élément** boîte de dialogue.

 \<VSTemplate> \<TemplateData> \<SupportsCodeSeparation>

## <a name="syntax"></a>Syntaxe

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans le **nouveau projet** ou **un nouvel élément** boîte de dialogue.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être `true` ou `false`indiquant ou non la **placer le code dans un fichier distinct** case à cocher est activée dans le **ajouter un nouvel élément** boîte de dialogue.

## <a name="remarks"></a>Notes
 `SupportsCodeSeparation` est un élément facultatif. La valeur par défaut est `false`.

 Le `SupportsCodeSeparation` élément est uniquement disponible pour les modèles d’élément Web.

 Séparation de code, ou le modèle de page code-behind, vous permet de conserver le balisage dans un fichier et le code de programmation dans un autre fichier. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et autres langages .NET utilisent ce modèle.

## <a name="example"></a>Exemple
 L’exemple suivant spécifie pour afficher le **placer le code dans un fichier distinct** option.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
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