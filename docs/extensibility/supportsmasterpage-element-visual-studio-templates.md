---
title: Élément SupportsMasterPage (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément SupportsMasterPage et sur la façon dont il spécifie si la case à cocher sélectionner la page maître est activée ou non dans la boîte de dialogue Ajouter un nouvel élément.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e9509d7bc0f8141b01ed1a0a600fa5d77a6d6916
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839374"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage, élément (modèles Visual Studio)
Spécifie si la case à cocher **Sélectionner la page maître** est activée ou non dans la boîte de dialogue **Ajouter un nouvel élément** .

 \<VSTemplate> \<TemplateData>
 \<SupportsMasterPage>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Spécifie les données qui classent le modèle et définit son affichage dans la boîte de dialogue **nouveau projet** ou **nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être `true` ou `false` , indiquant si la case à cocher **Sélectionner la page maître** est activée ou non dans la boîte de dialogue **Ajouter un nouvel élément** .

## <a name="remarks"></a>Remarques
 `SupportsMasterPage` est un élément facultatif. La valeur par défaut est `false`.

 L' `SupportsMasterPage` élément est uniquement disponible pour les modèles d’élément Web.

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées pour un projet Web qui prend en charge une page maître.

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
