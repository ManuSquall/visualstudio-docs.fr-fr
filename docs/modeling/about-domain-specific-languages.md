---
title: À propos des langues spécifiques au domaine | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 89293e0b684881767b6357b88469dc69ddc71902
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="about-domain-specific-languages"></a>À propos des langages spécifiques à un domaine

Contrairement à une langue à usage général, tel que c# ou UML, un langage spécifique à un domaine (DSL) est conçu pour exprimer des instructions dans un espace de problème particulier, ou un domaine.  
  
DSL connus inclure des expressions régulières et SQL. Chaque DSL est préférable à une langue à usage général pour décrire les opérations sur les chaînes de texte ou une base de données, mais bien pire permettant de décrire des idées qui sont en dehors de sa propre étendue. Des branches ont également leurs propres DSL. Par exemple, dans le secteur des télécommunications, appelez description langues sont couramment utilisées pour spécifier la séquence d’états dans un appel téléphonique et dans l’air de secteur du voyage une norme que DSL est utilisé pour décrire les réservations de vol.  
  
Votre entreprise et votre projet traitent également jeux spéciaux de concepts qui pourraient être décrits avec DSL. Par exemple, vous pouvez définir une DSL pour l’une de ces applications :  
  
-   Plan des chemins d’accès de navigation d’un site Web.  
  
-   Schémas de câblage pour des composants électroniques.  
  
-   Réseaux des tapis roulants et matériel pour un aéroport de manutention de bagages.  
  
Lorsque vous concevez une DSL, vous définissez un *classe de domaine* pour chacun des concepts importants dans le domaine, par exemple une page Web, feu ou aéroport archivage du support. Vous définissez *relations de domaine* comme lien hypertexte, câble ou un tapis roulant pour relier les concepts.  
  
Créent des utilisateurs de votre DSL *modèles.* Les modèles sont *instances* la DSL. Par exemple, elles décrivent un site Web particulier, ou le câblage d’un périphérique particulier, ou le système dans un aéroport déterminé de manutention de bagages.  
  
Vos utilisateurs peuvent afficher un modèle sous la forme d’un diagramme ou un Windows form. Les modèles peuvent également être affichés en tant que XML, qui est la façon dont elles sont stockées. Lorsque vous définissez une DSL, vous définir comment les instances de chaque classe de domaine et chaque relation apparaissent sur l’écran de l’utilisateur. DSL par défaut s’affiche comme une collection d’icônes ou de rectangles reliées par des flèches.  
  
L’illustration suivante montre un modèle petit dans DSL schématique :  
  
![Modèle d’arbre généalogique Tudor](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
## <a name="what-you-can-do-with-dsls"></a>Ce que vous pouvez faire avec DSL  

Une application classique d’une DSL est pour générer du code de programme ou d’autres artefacts. Lorsque vous définissez votre DSL, vous pouvez définir *modèles de texte* qui lire un modèle de la DSL et générer des fichiers texte.  
  
Par exemple, vous pouvez écrire des modèles qui prennent un plan d’aéroport et génèrent une partie du logiciel pour les bagages de gestion, ainsi que certains documents utilisateur qui décrivent le plan.  
  
Lorsque vous avez défini une DSL, vous pouvez le distribuer à d’autres utilisateurs qui peuvent l’installer sur leurs propres ordinateurs. Les utilisateurs de votre DSL peuvent créer et modifier des modèles dans Visual Studio.  
  
Vous pouvez également définir des commandes de menu et autres outils permettant aux utilisateurs de modifier la DSL, contraintes de validation pour garantir la DSL est utilisée correctement, et les modèles d’élément permettant aux utilisateurs de créent de nouvelles instances. Vous pouvez encapsuler un ou plusieurs DSL avec leurs outils et d’autres extensions de Visual Studio comme un ensemble intégré.  
  
En règle générale, un langage spécifique à un domaine est créé quand une équipe de développement doit écrire un code similaire à plusieurs produits. Par exemple, une entreprise spécialisée dans les systèmes de manutention de bagages peut définir une DSL de suivi de bagages à partir duquel ils peuvent générer le code pour chaque installation. Les avantages de la DSL sont qu’il puissent être reconnus par leurs clients, que le code généré à partir de celui-ci est fiable, et que le système peut être rapidement mis à jour si l’évolution des besoins des clients.  
  
[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] vous permet de créer un langage spécifique à un domaine qui contient votre propre concepteur graphique et la notation de votre propre schéma et ensuite utiliser le langage pour générer le code source approprié pour chaque projet.  
  
## <a name="domain-specific-development"></a>Développement de spécifique à un domaine

Développement de spécifique à un domaine consiste à identifier les parties de vos applications qui peuvent être modélisées en utilisant un langage spécifique à un domaine, puis construction de la langue et à son déploiement sur les développeurs d’applications. Les développeurs d’utilisent le langage spécifique à un domaine pour construire des modèles qui sont spécifiques à leurs applications, utiliser les modèles pour générer le code source, puis utiliser le code source pour développer des applications.  

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspects du développement de graphique spécifique à un domaine

Un langage spécifique à un domaine graphique doit inclure les fonctionnalités suivantes :  
  
- Notation  
  
- Modèle de domaine  
  
- Génération de l’artefact  
  
- Sérialisation  
  
- Intégration à Visual Studio  
  
### <a name="notation"></a>Notation

Un langage spécifique à un domaine doit avoir un ensemble relativement peu volumineux d’éléments qui peuvent être définis et étendus pour représenter des constructions spécifiques à un domaine. Une notation se compose de formes, qui représentent les éléments, et de connecteurs, qui représentent les relations entre les éléments, sur une surface du diagramme. Dans [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], les formes peuvent être étendus et optimisés pour représenter les éléments de votre langage spécifique à un domaine.  
  
### <a name="domain-model"></a>Modèle de domaine

Un langage spécifique à un domaine doit combiner l’ensemble des éléments et les relations entre eux dans une grammaire cohérente. Il doit également définir si les combinaisons d’éléments et les relations sont valides. Par exemple, les langages de programmation empêchent généralement l’héritage circulaire, dans laquelle une classe est dérivée d’une classe de seconde et la deuxième classe est dérivée de la première classe. Contraintes peuvent également être utilisées pour exprimer la logique métier, par exemple, une personne ne peut pas être un dépendant de lui-même. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utilise les contraintes pour exprimer les types de restrictions nécessitant plus des langages spécifiques à un domaine.  
  
### <a name="artifact-generation"></a>Génération de l’artefact

Un des principaux objectifs d’un langage spécifique à un domaine consiste à générer un artefact, par exemple, code source, un fichier XML ou autres données utilisables. En règle générale, une modification dans le modèle signifie une modification de l’artefact. Vous pouvez utiliser [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] pour générer des artefacts et régénérer les lorsque vous modifiez le modèle.  
  
### <a name="serialization"></a>Sérialisation

Un langage spécifique à un domaine doit être conservé dans une forme qui peut être modifiée, enregistrée, fermée et rechargée. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utilise un format XML qui vous permet de définir et personnaliser la façon dont votre langage spécifique à un domaine est sérialisé ou rendues persistantes.  
  
### <a name="integration-with-visual-studio"></a>Intégration à Visual Studio

Étant donné que [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] est hébergé dans Visual Studio, elle s’étend plusieurs fenêtres de Visual Studio et des contrôles. Il vous permet également de personnaliser le comportement des commandes de menu, des éléments de boîte à outils et autres éléments de l’interface utilisateur.  
  
Vous pouvez également créer un adaptateur de Bus pour votre langage spécifique à un domaine. Cet adaptateur vous permet d’un modèle de référence et des éléments au sein d’un modèle et vous permet de que écrire du code qui peut accéder et mettre à jour une instance de la DSL. À l’aide d’un mécanisme puissant Bus de modèles, vous pouvez écrire des extensions Visual Studio qui fonctionnent avec plusieurs modèles. Vous pouvez également écrire des applications autonomes qui fonctionnent avec les modèles. Pour plus d’informations, consultez [intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## <a name="benefits-of-domain-specific-development"></a>Avantages du développement de spécifique à un domaine

Un langage spécifique à un domaine peut fournir les avantages suivants :  
  
- Contient des constructions qui correspondent exactement à l’espace du problème.  
  
     Contrairement aux langages à usage général, un langage spécifique à un domaine se compose des éléments et des relations qui représentent directement la logique de l’espace du problème. Par exemple, une application d’assurance doit inclure les éléments des stratégies et les revendications. Un langage spécifique à un domaine facilite la conception de l’application et de rechercher et de corriger les erreurs de logique.  
  
- Permet de non-développeurs et les personnes qui ne connaissent pas le domaine comprendre la conception générale.  
  
     En utilisant un langage spécifique à un domaine graphique, vous pouvez créer une représentation visuelle du domaine afin que non-les développeurs peuvent facilement comprendre la conception de l’application.  
  
- Facilite la création d’un prototype de l’application finale.  
  
     Les développeurs peuvent utiliser le code qui génère de leur modèle pour créer une application de prototype qu’ils peuvent fournir aux clients.  
  
## <a name="the-process-of-domain-specific-development"></a>Le processus de développement de spécifique à un domaine

La plupart des équipes de développement logiciel qui utilisent des langages spécifiques à un domaine suivent ces étapes pour créer et utiliser leurs modèles :  
  
-   L’équipe permet de différencier les parties variables du domaine à partir des éléments qui ne changent jamais.  
  
-   Les développeurs d’écrire du code pour les parties fixes et conserver les points d’extension pour les parties variables.  
  
-   Le responsable du développement logiciel ou l’architecte crée un langage spécifique à un domaine qui incorpore les modèles de conception des parties du domaine et les points d’extension pour les parties variables fixes.  
  
-   Le responsable du développement logiciel ou l’architecte déploie le langage spécifique à un domaine pour les développeurs de diverses applications qui l’équipe de produit.  
  
-   Chaque développeur crée un modèle qui s’applique à l’application spécifique.