---
title: Référence API pour les modèles de texte T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ea0b136659b57b8430a355b4e231423c5e55b2b9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="api-reference-for-t4-text-templates"></a>Référence API pour les modèles de texte T4

L’API de création de modèles de texte vous permet d’appeler et de personnaliser la transformation de [modèles de texte](../modeling/code-generation-and-t4-text-templates.md).

## <a name="namespaces"></a>Espaces de noms

|Espace de noms|Objectif|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.TextTemplating>|Contient des classes pour la fonctionnalité de transformation de modèle de texte. Le moteur de transformation de modèle de texte est intégré à Visual Studio et transforme les fichiers de modèle de texte en fichiers de sortie texte généré.|
|<xref:Microsoft.VisualStudio.TextTemplating.Modeling>|Fournit des fonctionnalités de transformation liées à des modèles UML et des langages spécifiques à un domaine, comme l’accès au texte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus.|
|<xref:Microsoft.VisualStudio.TextTemplating.VSHost>|Fournit l’accès au service de création de modèles de texte dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|