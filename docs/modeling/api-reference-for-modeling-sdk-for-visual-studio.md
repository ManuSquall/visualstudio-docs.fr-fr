---
title: Référence des API pour la modélisation du Kit de développement logiciel
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5f5ecea7313610ff89616cd1c9373130d22a4176
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930312"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Référence des API pour le Kit de développement logiciel de modélisation pour Visual Studio

Le Visual Studio Visualization and Modeling SDK fournit la plateforme sur laquelle reposent vos outils de langages spécifiques à un domaine (DSL).

Cette section contient des documents de référence pour les espaces de noms qui ont des noms qui commencent par « Microsoft.VisualStudio.Modeling ».

|Espace de noms|Contenu|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Classes telles que l’élément de modèle, qui est la classe de base de toutes les classes de domaine que vous définissez dans une solution DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Classes qui font partie d’une définition DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Les outils de mesure de modèle Observateur de Store et les performances.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Classes telles que ShapeElement, qui est la classe de base de toutes les formes que vous définissez dans une solution DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Méthodes de mouvement et la sélection.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|L’API du Concepteur de définition DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classes internes du Concepteur de définition DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attributs qui vous permettent d’étendre le concepteur DSL avec des commandes, mouvements et la validation.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Méthodes d’extension pour l’élément de modèle qui implémentent l’extensibilité de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Attributs de l’extensibilité|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Vous permet de rendre des parties d’un modèle en lecture seule.|
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|L’API de Modelbus, qui vous permet d’intégrer des modèles différents.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|La boîte de dialogue qui permet aux utilisateurs d’accéder à des modèles et des éléments pour créer les références Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Le service de sélecteur.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Infrastructure d’adaptateurs ModelBus de Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|La boîte de dialogue de sélecteur qui permet aux utilisateurs d’accéder à des modèles et des éléments pour créer les références Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|L’interface entre plusieurs DSL et Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Vous permet de définir des commandes du menu contextuel (contexte).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Vous permet de définir des contraintes de validation.|

## <a name="see-also"></a>Voir aussi

- [Personnalisation d’une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)
