---
title: "Vue d&#39;ensemble des outils de langage sp&#233;cifique &#224; un domaine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine"
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 54
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 54
---
# Vue d&#39;ensemble des outils de langage sp&#233;cifique &#224; un domaine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Outils de languages spécifique au domaine \(outils DÉSOLÉ\), hébergés dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous permettent de concevoir un langage spécifique au domaine puis générer tout ce que les utilisateurs doivent posséder pour créer des modèles basées sur la langue.  
  
 Les outils suivants sont inclus dans des outils DÉSOLÉ :  
  
-   Un Assistant de projet qui utilise des modèles de solution pour vous aider démarrez développer votre langage spécifique au domaine.  
  
-   Un concepteur graphique pour créer et modifier votre définition de langage spécifique à un domaine.  
  
-   Un moteur de validation pour s'assurer que la définition de langage spécifique au domaine est bien formée, et affiche des erreurs et des avertissements en cas de problème.  
  
-   Un générateur de code qui prend une définition de langage spécifique au domaine comme entrée et produit le code source comme sortie.  
  
## Le langage DÉSOLÉ ordinateurs la solution  
 L'Assistant concepteur spécifique au domaine fournit des modèles de solution :  
  
-   Flux de travail  
  
-   diagrammes de classes  
  
-   langage minimal  
  
-   modèles composants  
  
-   WPF minimal  
  
-   Windows.Forms minimal  
  
-   Bibliothèque DÉSOLÉ  
  
 Pour plus d'informations, consultez [Choix d'un modèle de solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 L'Assistant crée une solution de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui a des projets suivants :  
  
-   DÉSOLÉ  
  
     Le projet DÉSOLÉ des outils définit le langage spécifique au domaine et sa modification et traiter.  
  
-   **DslPackage**  
  
     Le projet de DslPackage détermine comment les outils de languages s'intègrent aux [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Le langage DÉSOLÉ ordinateurs l'interface graphique  
 Vous pouvez utiliser l'interface graphique d'outils DÉSOLÉ pour ajouter des éléments et des relations à votre langage spécifique au domaine.  Après avoir ajouté les éléments, vous pouvez définir leur apparence en les mappant aux formes, en personnalisant les couleurs, et en ajoutant des éléments décoratifs.  Vous pouvez également ajouter des éléments à la boîte à outils.  
  
## Validation dans les outils DÉSOLÉ  
 Le langage DÉSOLÉ fournit un niveau de validation pour vérifier que le modèle de domaine répond aux conditions de base pour la génération de code.  En général, lorsque vous créez votre propre langage spécifique au domaine, vous devez ajouter votre propre validation pour exprimer vos règles de logique métier.  Pour plus d'informations sur la validation personnalisée, consultez l' [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).  
  
 Nous vous recommandons de valider du langage spécifique au domaine souvent lorsque vous le créez.  Si votre langage spécifique au domaine a des erreurs de validation, vous ne pouvez pas générer de code source.  Le processus de génération de code source des modèles est exécuté en cliquant sur **Transformer tous les modèles** dans la barre d'outils de l'explorateur de solutions.  Chaque fois que vous modifiez la définition de langage, veillez également à **Transformer tous les modèles**.  Pour plus d'informations, consultez [Comment : créer une solution de langage spécifique à un domaine](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## Personnalisation des outils DÉSOLÉ  
 Vous pouvez écrire du code supplémentaire pour affiner le comportement du modèle et de définir des contraintes sur votre langage.  Si nécessaire, vous pouvez apporter des modifications significatives en modifiant les modèles de texte.  
  
## Distribuer votre solution DÉSOLÉ  
 Les outils DÉSOLÉ génère un package qui est hébergé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Le package affiche une boîte à outils, un explorateur DÉSOLÉ, et d'autres éléments d'interface utilisateur qui permettent aux utilisateurs de créer des modèles à l'aide de votre langage spécifique au domaine.  
  
 Lorsque vous générez et exécutez le code DÉSOLÉ ordinateurs la solution dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], une deuxième instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous indique comment votre langage spécifique au domaine la recherche à l'utilisateur. Après vous être assuré que tout fonctionne correctement, vous pouvez distribuer le fichier d' `.vsix` que vous trouverez dans le dossier build du projet de DslPackage.  Ce fichier peut être utilisé pour installer le domaine \(comme une extension de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sur d'autres ordinateurs.  Pour plus d'informations, consultez [Déploiement de solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).  
  
## Voir aussi  
 [L'Instance expérimentale](../extensibility/the-experimental-instance.md)   
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)