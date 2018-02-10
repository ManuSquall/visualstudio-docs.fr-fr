---
title: "Kit de développement logiciel de modélisation pour Visual Studio - langages spécifiques à un domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-modeling
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1edb30221d85f8e634a9d618d50cd1e0b772b69a
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Kit de développement logiciel de modélisation pour Visual Studio - Langages spécifiques à un domaine
À l’aide du Kit de développement logiciel de modélisation pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez créer des outils de développement puissant basé sur le modèle que vous pouvez intégrer à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. De la même manière, vous pouvez créer une ou plusieurs définitions de modèle et la/les intégrer dans un ensemble d'outils.  
  
 La définition d'un modèle créé pour représenter les concepts de votre secteur d'activité est au cœur du MSDK. Vous pouvez encadrer le modèle de divers outils, tels qu'une vue schématique, la capacité à générer du code et autres artefacts, les commandes pour transformer le modèle, et la possibilité d'interagir avec le code et les autres objets dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Lorsque vous développez le modèle, vous pouvez le combiner avec d'autres modèles et outils et créer un ensemble d'outils puissant centré sur le développement.  
  
 MSDK vous permet de développer un modèle rapidement sous forme de langage spécifique à un domaine (DSL). Commencez par utiliser un éditeur spécialisé pour définir un schéma ou une syntaxe abstraite avec une notation graphique. À partir de cette définition, MSDK génère :  
  
-   une implémentation du modèle avec une API fortement typée qui s'exécute dans un magasin basé sur la transaction ;  
  
-   un explorateur basé sur l'arborescence ;  
  
-   un éditeur graphique dans lequel les utilisateurs peuvent afficher le modèle, ou une partie du modèle que vous définissez ;  
  
-   des méthodes de sérialisation qui enregistrent les modèles lisibles au format XML ;  
  
-   des fonctionnalités pour générer du code de programme et autres artefacts à l'aide de création de modèles de texte.  
  
 Toutes ces fonctionnalités peuvent être personnalisées et étendues. Les extensions sont intégrées de telle façon que vous pouvez toujours mettre à jour la définition DSL et générer de nouveau les fonctionnalités sans perdre ces extensions.  
  
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
 [Billets de blog connexes](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
  
 Pour obtenir des conseils sur les techniques avancées et la résolution des problèmes, visitez [forum Visual Studio DSL et d’extensibilité des outils de modélisation](http://go.microsoft.com/fwlink/?LinkID=186074).  
  
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
