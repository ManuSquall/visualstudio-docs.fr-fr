---
title: Élément SupportsCodeSeparation (modèles Visual Studio) | Microsoft Docs
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
ms.openlocfilehash: 9e68516a798bcd4d1437ab504c09b4cc529eb889
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719430"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation, élément (modèles Visual Studio)
Spécifie si la case à cocher **Placer le code dans un fichier distinct** est activée dans la boîte de dialogue **Ajouter un nouvel élément** .

 \<VSTemplate > \<TemplateData > \<SupportsCodeSeparation >

## <a name="syntax"></a>Syntaxe

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun(e).

### <a name="child-elements"></a>Éléments enfants
 Aucun(e).

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle dans une catégorie et définit son affichage dans la boîte de dialogue **nouveau projet** ou **nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être `true` ou `false`, ce qui indique si la case à cocher **Placer le code dans un fichier distinct** est activée dans la boîte de dialogue **Ajouter un nouvel élément** .

## <a name="remarks"></a>Notes
 `SupportsCodeSeparation` est un élément facultatif. La valeur par défaut est `false`.

 L’élément `SupportsCodeSeparation` est disponible uniquement pour les modèles d’élément Web.

 La séparation du code, ou le modèle de page code-behind, vous permet de conserver le balisage dans un fichier et le code de programmation dans un autre fichier. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et d’autres langages .NET utilisent ce modèle.

## <a name="example"></a>Exemple
 L’exemple suivant spécifie l’affichage de l’option **Placer le code dans un fichier distinct** .

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