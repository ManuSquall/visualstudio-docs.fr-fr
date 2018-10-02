---
title: Vue d’ensemble des outils Domain-Specific Language | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 694ebbc73b531f4fab1c8b2f9621e14f4145bd70
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493428"
---
# <a name="overview-of-domain-specific-language-tools"></a>Vue d'ensemble des outils de langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue d’ensemble d’outils de langage spécifique à un domaine](https://docs.microsoft.com/visualstudio/modeling/overview-of-domain-specific-language-tools).  
  
Outils Domain-Specific Language (outils DSL), qui sont hébergées sur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], laissez un langage spécifique à un domaine de conception et de puis générer tout ce que les utilisateurs doivent disposer pour créer des modèles qui sont basés sur le langage.  
  
 Les outils suivants sont inclus dans les outils DSL :  
  
-   Un Assistant de projet qui utilise des modèles de solution différents pour vous aider à commencer à développer votre langage spécifique à un domaine.  
  
-   Un concepteur graphique pour créer et modifier votre définition de langage spécifique à un domaine.  
  
-   Un moteur de validation qui permet de s’assurer que la définition de langage spécifique à un domaine est correctement formée et affiche les erreurs et avertissements s’il existe des problèmes.  
  
-   Un générateur de code qui prend une définition de langage spécifique à un domaine en tant qu’entrée et génère le code source en tant que sortie.  
  
## <a name="the-dsl-tools-solution"></a>La Solution d’outils DSL  
 L’Assistant Concepteur Domain-Specific fournit les modèles de solution suivants :  
  
-   Flux de tâches  
  
-   Diagrammes de classes  
  
-   Langage minimal  
  
-   Modèles de composants  
  
-   WPF minimal  
  
-   Windows.Forms minimal  
  
-   Bibliothèque DSL  
  
 Pour plus d’informations, consultez [choix d’un modèle de Solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 L’Assistant crée un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solution qui contient les projets suivants :  
  
-   DSL  
  
     Le projet Dsl définit le langage spécifique à un domaine et ses outils d’éditions et de traitement.  
  
-   **DslPackage**  
  
     Le projet DslPackage détermine comment intègrent les outils de langage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>L’Interface graphique des outils DSL  
 Vous pouvez utiliser l’interface graphique d’outils DSL pour ajouter des éléments et des relations à votre langage spécifique à un domaine. Une fois que vous avez ajouté les éléments, vous pouvez définir leur apparence en les mappant aux formes, la personnalisation des couleurs et l’ajout d’éléments décoratifs. Vous pouvez également ajouter les éléments à la boîte à outils.  
  
## <a name="validation-in-dsl-tools"></a>Validation dans les outils DSL  
 DSL offre un niveau de validation pour vous assurer que le modèle de domaine répond aux exigences de base pour la génération de code. En règle générale, lorsque vous créez votre propre langage spécifique à un domaine, vous devez ajouter votre propre validation pour exprimer vos règles de logique métier. Pour plus d’informations sur la validation personnalisée, consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).  
  
 Nous vous recommandons de valider votre langage spécifique à un domaine souvent lors de sa création. Si votre langage spécifique à un domaine comporte des erreurs de validation, vous ne pouvez pas générer le code source. Le processus de génération de code source à partir des modèles est effectué en cliquant sur **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions. Chaque fois que vous modifiez la définition de langage, veillez également à **transformer tous les modèles**. Pour plus d’informations, consultez [Comment : créer une Solution de langage spécifique à un domaine](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Personnalisation des outils DSL  
 Vous pouvez fournir un code supplémentaire pour affiner le comportement du modèle et définir des contraintes sur votre langue. Si nécessaire, vous pouvez apporter des modifications significatives en modifiant les modèles de texte.  
  
## <a name="distributing-your-dsl-solution"></a>Distribuer votre Solution DSL  
 Outils DSL génère un package qui est hébergé dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le package affiche une boîte à outils, un Explorateur DSL et autres éléments d’interface utilisateur qui permettent aux utilisateurs de créer des modèles à l’aide de votre langage spécifique à un domaine.  
  
 Lorsque vous générez et exécutez la solution d’outils DSL [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], une deuxième instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vous montre comment votre langage spécifique à un domaine à l’utilisateur de la langue. Après avoir vérifié que tout fonctionne correctement, vous pouvez distribuer le `.vsix` fichier que vous trouverez dans le dossier de génération du projet DslPackage. Ce fichier peut être utilisé pour installer la solution DSL comme un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extension sur d’autres ordinateurs.  Pour plus d’informations, consultez [déploiement de Solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’Instance expérimentale](../extensibility/the-experimental-instance.md)   
 [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



