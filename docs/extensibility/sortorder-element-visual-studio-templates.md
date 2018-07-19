---
title: SortOrder, élément (modèles Visual Studio) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b963b6e74b7c24d31ddc611407df22380ff8bb60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140321"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder, élément (modèles Visual Studio)
Spécifie une valeur qui est utilisée pour organiser le modèle, parmi d’autres modèles dans la même catégorie, telle qu’elle apparaît, que ce soit le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<SortOrder >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 Un `integer` qui représente la valeur d’ordre de tri.  
  
## <a name="remarks"></a>Notes  
 `SortOrder` est un élément facultatif. La valeur par défaut est 100 et toutes les valeurs doivent être des multiples de 10.  
  
 Le `SortOrder` élément est ignoré pour les modèles créés par l’utilisateur. Tous les modèles créés par l’utilisateur sont triés par ordre alphabétique.  
  
 Les modèles qui ont des valeurs d’ordre de tri faible apparaissent, que ce soit le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue avant les modèles qui ont des valeurs d’ordre de tri haute.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre les métadonnées d’une norme [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modèle de classe.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Dans cet exemple, le `SortOrder` élément est relativement élevé. Il est probable que les autres [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] auront des modèles d’élément un `SortOrder` valeur inférieure à `290` et apparaîtront avant ce modèle dans le **un nouvel élément** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)