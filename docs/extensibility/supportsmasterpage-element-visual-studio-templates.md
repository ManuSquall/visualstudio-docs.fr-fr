---
title: SupportsMasterPage Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 384672303d00b72431820b98fa02d09e440a1de5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699454"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage, élément (modèles Visual Studio)
Précise si la case à cocher **Select Master Page** est activée sur la case de dialogue Add New **Item.**

 \<VSTemplate> \<TemplateData> \<supportsMasterPage>

## <a name="syntax"></a>Syntaxe

```
<SupportsMasterPage> true/false </SupportsMasterPage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Spécifie les données qui catégorisent le modèle et définissent la façon dont il s’affiche dans la boîte de dialogue **Du nouveau projet** ou du nouvel **élément.**|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit `true` `false`être soit ou, indiquant si oui ou non la case à cocher **Select Master Page** est activée sur la boîte de dialogue Add New **Item.**

## <a name="remarks"></a>Notes
 `SupportsMasterPage` est un élément facultatif. La valeur par défaut est `false`.

 L’élément `SupportsMasterPage` n’est disponible que pour les modèles d’objets Web.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées d’un projet Web qui comprend le soutien à une page maîtresse.

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
        <SupportsMasterPage>true</SupportsMasterPage>
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
