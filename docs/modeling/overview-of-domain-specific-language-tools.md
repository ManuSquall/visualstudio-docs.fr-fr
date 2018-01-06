---
title: "Vue d’ensemble des outils de langage spécifique à un domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: "54"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 394887f5da92e6325266167a0c79f717e0a3a31c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-domain-specific-language-tools"></a>Vue d'ensemble des outils de langage spécifique à un domaine
Outils de langage spécifique à un domaine (outils DSL), qui sont hébergés dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], laissez concevoir un langage spécifique à un domaine et de générer tout ce que les utilisateurs doivent disposer pour créer des modèles qui sont basées sur le langage.  
  
 Les outils suivants sont inclus dans les outils DSL :  
  
-   Un Assistant de projet qui utilise des modèles de l’autre solution pour vous aider à commencer à développer votre langage spécifique à un domaine.  
  
-   Un concepteur graphique pour créer et modifier votre définition de langage spécifique à un domaine.  
  
-   Un moteur de validation qui permet de s’assurer que la définition de langage spécifique à un domaine est correcte et affiche les erreurs et avertissements s’il existe des problèmes.  
  
-   Générateur de code qui prend une définition de langage spécifique à un domaine en tant qu’entrée et génère le code source en tant que sortie.  
  
## <a name="the-dsl-tools-solution"></a>La Solution d’outils DSL  
 L’Assistant de concepteur spécifique à un domaine fournit les modèles de solution suivants :  
  
-   Flux de tâches  
  
-   Diagrammes de classes  
  
-   Langage minimale  
  
-   Modèles de composants  
  
-   WPF minimale  
  
-   Windows.Forms minimale  
  
-   Bibliothèque DSL  
  
 Pour plus d’informations, consultez [choisir un modèle de Solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 L’Assistant crée un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution qui contient les projets suivants :  
  
-   DSL  
  
     Le projet Dsl définit le langage spécifique à un domaine et ses outils de modification et de traitement.  
  
-   **DslPackage**  
  
     Le projet DslPackage détermine comment intégrant les outils de langage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>L’Interface graphique d’outils DSL  
 Vous pouvez utiliser l’interface graphique outils DSL pour ajouter des éléments et des relations à votre langage spécifique à un domaine. Après avoir ajouté les éléments, vous pouvez définir leur apparence en les mappant aux formes, personnaliser les couleurs et l’ajout des éléments décoratifs. Vous pouvez également ajouter les éléments à la boîte à outils.  
  
## <a name="validation-in-dsl-tools"></a>Validation des outils DSL  
 DSL fournit un niveau de validation pour vous assurer que le modèle de domaine répond aux exigences de base pour la génération de code. En règle générale, lorsque vous créez votre propre langage spécifique à un domaine, vous devez ajouter votre propre validation pour exprimer vos règles de logique métier. Pour plus d’informations sur la validation personnalisée, consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).  
  
 Nous vous recommandons de valider votre langage spécifique à un domaine souvent lors de sa création. Si votre langage spécifique à un domaine comporte des erreurs de validation, vous ne pouvez pas générer de code source. Le processus de génération de code source à partir des modèles est effectué en cliquant sur **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions. Chaque fois que vous modifiez la définition de langage, veillez également à **transformer tous les modèles**. Pour plus d’informations, consultez [Comment : créer une Solution de langage spécifique à un domaine](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Personnalisation des outils DSL  
 Vous pouvez fournir un code supplémentaire pour affiner le comportement du modèle et de définir des contraintes sur votre langue. Si nécessaire, vous pouvez apporter des modifications importantes en modifiant les modèles de texte.  
  
## <a name="distributing-your-dsl-solution"></a>Distribution de votre Solution DSL  
 Outils DSL génère un package qui est hébergé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le package affiche une boîte à outils, un Explorateur DSL et autres éléments d’interface utilisateur qui permettent aux utilisateurs de créer des modèles à l’aide de votre langage spécifique à un domaine.  
  
 Lorsque vous générez et exécuter la solution outils DSL dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], une deuxième instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous montre comment votre langage spécifique à un domaine à l’utilisateur de la langue. Après avoir vérifié que tout fonctionne correctement, vous pouvez distribuer le `.vsix` fichier que vous trouverez dans le dossier de génération du projet DslPackage. Ce fichier peut être utilisé pour installer la DSL comme un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extension sur d’autres ordinateurs.  Pour plus d’informations, consultez [déploiement de Solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’Instance expérimentale](../extensibility/the-experimental-instance.md)   
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)