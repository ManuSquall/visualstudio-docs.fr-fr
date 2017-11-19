---
title: "Référence des API pour la modélisation du Kit de développement logiciel pour Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: "8"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 1acbeb95ed7fa59fd64feefe050debc0ce9b6461
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Référence des API pour le Kit de développement logiciel de modélisation pour Visual Studio
Le Visual Studio Visualization and Modeling SDK fournit la plateforme sur laquelle reposent vos outils de langages de spécifique à un domaine (DSL).  
  
 Cette section contient des documents de référence pour les espaces de noms qui ont des noms qui commencent par « Microsoft.VisualStudio.Modeling ».  
  
|Espace de noms|Contenu|  
|---------------|-------------|  
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Classes telles que l’élément de modèle, qui est la classe de base de toutes les classes de domaine que vous définissez dans DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Classes qui font partie d’une définition DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Les outils de mesure de modèle Observateur de magasin et les performances.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Classes telles que ShapeElement, qui est la classe de base de toutes les formes que vous définissez dans DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Méthodes de mouvements et la sélection.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|L’API du Concepteur de définition DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classes internes du Concepteur de définition DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attributs qui vous permettent d’étendre le concepteur DSL avec les commandes, de mouvements et de validation.|  
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Méthodes d’extension pour l’élément de modèle qui implémentent l’extensibilité du DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Attributs d’extensibilité|  
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Vous pouvez effectuer des parties d’un modèle en lecture seule.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|L’API de Modelbus, qui vous aide à intégrer des modèles différents.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|La boîte de dialogue qui permet aux utilisateurs d’accéder à des modèles et des éléments pour créer des références de Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Le service de sélecteur.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Infrastructure d’adaptateurs ModelBus pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|La boîte de dialogue Sélecteur qui permet aux utilisateurs d’accéder à des modèles et des éléments pour créer des références de Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|L’interface entre plusieurs DSL et [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Permet de définir des commandes de menu contextuel.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Permet de définir des contraintes de validation.|  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation d’une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)
