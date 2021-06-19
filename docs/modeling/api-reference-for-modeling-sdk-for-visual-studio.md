---
title: Informations de référence sur l’API pour modeler SDK
description: Découvrez comment le kit de développement logiciel (SDK) de visualisation et de modélisation de Visual Studio fournit la plate-forme sur laquelle vos outils DSL (Domain-Specific Languages) sont générés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9603ace5751443c04d0a7503a43e08c044269817
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385459"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Référence des API pour le Kit de développement logiciel de modélisation pour Visual Studio

Le kit de développement logiciel (SDK) de visualisation et de modélisation de Visual Studio fournit la plate-forme sur laquelle vos outils DSL (langage spécifique à un domaine) sont générés.

Cette section contient des documents de référence pour les espaces de noms dont le nom commence par « Microsoft. VisualStudio. Modeling ».

|Espace de noms|Contenu|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Les classes telles que ModelElement, qui est la classe de base de toutes les classes de domaine que vous définissez dans une solution DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Les classes qui font partie d’une définition DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Visionneuse du magasin de modèles et outils de mesure des performances.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Les classes telles que ShapeElement, qui est la classe de base de toutes les formes que vous définissez dans un DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Méthodes de mouvement et de sélection.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|API du concepteur de définitions DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classes internes du concepteur de définitions DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attributs qui vous permettent d’étendre le concepteur DSL avec les commandes, les gestes et la validation.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Méthodes d’extension pour ModelElement qui implémentent l’extensibilité DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Attributs d’extensibilité|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Vous permet de créer des parties d’un modèle en lecture seule.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|L’API ModelBus, qui vous permet d’intégrer différents modèles.|
|[Microsoft. VisualStudio. Modeling. Integration. Picker](/previous-versions/ee904394(v=vs.140))|La boîte de dialogue qui permet aux utilisateurs d’accéder aux modèles et aux éléments pour créer des références ModelBus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Service du sélecteur.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Infrastructure d’adaptateur ModelBus pour Visual Studio.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|Boîte de dialogue du sélecteur qui permet aux utilisateurs d’accéder aux modèles et aux éléments pour créer des références ModelBus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interface entre DSL et Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Vous permet de définir des commandes de menu de raccourci (contexte).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Vous permet de définir des contraintes de validation.|

## <a name="see-also"></a>Voir aussi

- [Personnalisation d'une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)
