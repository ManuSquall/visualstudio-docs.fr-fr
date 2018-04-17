---
title: AppliesTo, élément (modèles Visual Studio) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e27ee1ab0ba42a82d61e2adbe9fb4c6c81cbb48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo, élément (modèles Visual Studio)
Spécifie une expression facultative afin de la faire correspondre à une ou plusieurs fonctions. (consultez <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>). Les fonctions sont exposées par types de projet via la hiérarchie en tant que propriété <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5>. De cette manière, le modèle peut être partagé par plusieurs types de projets ayant des capacités applicables communes.  
  
 Cet élément est facultatif. Il peut y avoir au maximum une instance dans un fichier modèle. Cet élément permet uniquement à un modèle d'élément d'être déclaré comme applicable, en fonction des fonctionnalités du projet actif sélectionné. Il ne peut pas être utilisé pour rendre un modèle d'élément non applicable. Si `AppliesTo` est absent ou si l'expression ne permet pas de déclarer correctement, alors `TemplateID` ou `TemplateGroupID` est utilisé pour rendre le modèle applicable, comme avec les versions antérieures du produit.  
  
 Introduit pour la première fois dans Visual Studio 2013 Update 2. Pour faire référence à la version appropriée, consultez [faisant référence à des assemblys remis dans Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb).  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<AppliesTo >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
-   L’expression de fonctionnalité, tel que « (VisualC &#124; CSharp) + (MSTest &#124; NUnit) ».  
  
-   Le «&#124;» est l’opérateur OR.  
  
-   Les caractères « & » et « + » sont tous les deux des opérateurs AND.  
  
-   Le caractère « ! » est l'opérateur NOT.  
  
-   Les parenthèses forcent l'ordre de priorité de l'évaluation.  
  
-   Une expression null ou vide est évaluée comme une correspondance.  
  
-   Les fonctionnalités de projet peuvent être n’importe quel caractère excepté les caractères réservés : « ''  :;,+-*/\\! ~&#124;& %$@^()={} [] <> ? \t\b\n\r  
  
## <a name="example"></a>Exemple  
 L'exemple suivant indique trois modèles différents. `Template1` s'applique à tous les types de projet C# ou à n'importe quel autre type de projet qui prend en charge la fonctionnalité `WindowsAppContainer`. `Template2` s'applique à tous les projets C# de n'importe quel type. `Template3` s'applique aux projets C# qui ne sont pas des projets `WindowsAppContainer`.  
  
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
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)