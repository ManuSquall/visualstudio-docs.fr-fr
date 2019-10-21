---
title: Modeling SDK-langages spécifiques à un domaine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: 79
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b67f74397b8f3c3e410c4282d8a74b7309bc1bc9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668634"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Kit de développement logiciel de modélisation pour Visual Studio - Langages spécifiques à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En utilisant le kit de développement logiciel (SDK) de modélisation pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (MSDK), vous pouvez créer des outils de développement puissants basés sur des modèles, que vous pouvez intégrer à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Par exemple, les outils UML sont créés à l'aide du MSDK. De la même manière, vous pouvez créer une ou plusieurs définitions de modèle et la/les intégrer dans un ensemble d'outils.

 La définition d'un modèle créé pour représenter les concepts de votre secteur d'activité est au cœur du MSDK. Vous pouvez encadrer le modèle de divers outils, tels qu'une vue schématique, la capacité à générer du code et autres artefacts, les commandes pour transformer le modèle, et la possibilité d'interagir avec le code et les autres objets dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Lorsque vous développez le modèle, vous pouvez le combiner avec d'autres modèles et outils et créer un ensemble d'outils puissant centré sur le développement.

 MSDK vous permet de développer un modèle rapidement sous forme de langage spécifique à un domaine (DSL). Commencez par utiliser un éditeur spécialisé pour définir un schéma ou une syntaxe abstraite avec une notation graphique. À partir de cette définition, MSDK génère :

- une implémentation du modèle avec une API fortement typée qui s'exécute dans un magasin basé sur la transaction ;

- un explorateur basé sur l'arborescence ;

- un éditeur graphique dans lequel les utilisateurs peuvent afficher le modèle, ou une partie du modèle que vous définissez ;

- des méthodes de sérialisation qui enregistrent les modèles lisibles au format XML ;

- des fonctionnalités pour générer du code de programme et autres artefacts à l'aide de création de modèles de texte.

  Toutes ces fonctionnalités peuvent être personnalisées et étendues. Les extensions sont intégrées de telle façon que vous pouvez toujours mettre à jour la définition DSL et générer de nouveau les fonctionnalités sans perdre ces extensions.

## <a name="samples-and-the-latest-information"></a>Exemples et dernières informations
 [Télécharger le kit de développement logiciel Modeling SDK pour Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148)

 [Exemples](http://go.microsoft.com/fwlink/?LinkId=186128) pour le kit de développement logiciel de modélisation pour Visual Studio.

 Pour obtenir des conseils sur les techniques avancées et la résolution des problèmes, consultez le [Forum d’extensibilité des outils de modélisation de Visual Studio &](http://go.microsoft.com/fwlink/?LinkID=186074).

## <a name="in-this-section"></a>Dans cette section
 [Bien démarrer avec les langages spécifiques à un domaine](../modeling/getting-started-with-domain-specific-languages.md)

 [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md)

 [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)

 [Personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md)

 [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)

 [Fonctionnement du code DSL](../modeling/understanding-the-dsl-code.md)

 [Personnalisation du stockage de fichiers et de la sérialisation XML](../modeling/customizing-file-storage-and-xml-serialization.md)

 [Déploiement de solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md)

 [Création d’un langage spécifique à un domaine basé sur Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [Création d’un langage spécifique à un domaine basé sur WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [Guide pratique pour étendre le concepteur de langage spécifique à un domaine](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [Éditions de Visual Studio prises en charge pour le SDK de visualisation et de modélisation](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [Guide pratique pour migrer un langage spécifique à un domaine vers une nouvelle version](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [Informations de référence de l’API pour le SDK de modélisation pour Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
