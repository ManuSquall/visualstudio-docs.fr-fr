---
title: "&#192; propos des langages sp&#233;cifiques &#224; un domaine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine"
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 26
---
# &#192; propos des langages sp&#233;cifiques &#224; un domaine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contrairement à un langage à usage général tel que c\# ou l'UML, un langage spécifique au domaine est conçu \(DSL\) pour exprimer les instructions en espace particulier de problème, le champ ou.  
  
 Langages spécifiques à un domaine connu incluent des expressions régulières et SQL.  Chaque langage DÉSOLÉ est préférable d'un langage à usage général pour décrire des opérations de chaînes de texte ou une base de données, mais beaucoup plus médiocre pour décrire des idées qui sont en dehors de sa propre portée.  Les différentes industries ont également leur propre langages spécifiques à un domaine.  Par exemple, dans l'industrie des télécommunications, les langages de description d'appel sont largement utilisées pour spécifier la séquence des rapports dans un appel téléphonique, et de l'industrie de transports aériens une norme DÉSOLÉ est utilisé pour décrire des réservations de vol.  
  
 Votre entreprise et le projet traitent également des ensembles spéciaux de concepts qui peuvent être décrits par un langage spécifique à un domaine.  Par exemple, vous pouvez définir un DÉSOLÉ pour une de ces applications :  
  
-   Plan des chemins de navigation d'un site Web.  
  
-   Diagrammes de connexion pour les composants électroniques.  
  
-   Réseaux des tapis roulants et les appareils de manutention de bagages d'un aéroport.  
  
 Lorsque vous concevez un langage spécifique à un domaine, vous définissez *une classe de domaine* pour chacun des concepts importants dans le champ, tel qu'une page Web, une lampe, ou un comptoir d'aéroportuaire.  Vous définissez *des relations de domaine* telles que le lien hypertexte, le responsable, ou un tapis roulant pour lier les concepts ensemble.  
  
 Les utilisateurs de votre DÉSOLÉ créent *des modèles.* Les modèles sont *des instances* du langage spécifique à un domaine.  Par exemple, elles décrivent un site Web particulier, ou la transmission d'un appareil particulier, ou du système de gestion des bagages dans un aéroport particulier.  
  
 Vos utilisateurs peuvent afficher un modèle comme un diagramme ou comme un formulaire Windows.  Les modèles peuvent également être affichés en tant que XML, c'est\-à\-dire la manière dont elles sont enregistrées.  Lorsque vous définissez un langage spécifique à un domaine, vous définissez la façon dont les instances de chaque classe et relation de domaine apparaissent sur l'écran de l'utilisateur.  Un DÉSOLÉ classique est affiché comme une collection d'icônes ou de rectangles reliés par des flèches.  
  
 L'illustration suivante montre un petit modèle dans un domaine \(schématique :  
  
 ![Modèle d'arbre généalogique de la famille Tudor](~/docs/modeling/media/tudor_familytreemodel.png "Tudor\_FamilyTreeModel")  
  
## Les opérations réalisables avec langages spécifiques à un domaine  
 Une application classique d'un DÉSOLÉ est de générer du code de programme ou d'autres artefacts.  Lorsque vous définissez votre DÉSOLÉ, vous pouvez définir *des modèles de texte* qui indiquent un modèle du langage DÉSOLÉ et génèrent des fichiers texte.  
  
 Par exemple, vous pouvez écrire des modèles qui prennent un plan d'aéroport et génèrent une partie du logiciel pour la gestion des bagages, ainsi que certains documents utilisateur qui décrivent le plan.  
  
 Lorsque vous avez défini un DÉSOLÉ, vous pouvez la distribuer à d'autres utilisateurs qui pourront l'installer sur leur propre ordinateur.  Les utilisateurs de votre DÉSOLÉ peuvent créer et modifier des modèles dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Vous pouvez également définir des commandes de menu et d'autres outils que les utilisateurs d'aide modifient le DÉSOLÉ, les contraintes de validation pour vous aider à vous assurer que le langage DÉSOLÉ est utilisé correctement, et les modèles d'élément que les utilisateurs d'aide créent des instances.  Vous pouvez encapsuler un ou plusieurs langages spécifiques à un domaine avec leurs outils et d'autres extensions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comme package intégré.  
  
 En général, un langage spécifique au domaine est créé lorsqu'une équipe de développement doit écrire du code semblable pour plusieurs produits.  Par exemple, une société qui se spécialise dans les systèmes de manutention de bagages peut définir une piste DÉSOLÉ de bagages dont ils peuvent générer une partie du code pour chaque installation.  Les avantages du langage DÉSOLÉ sont qu'il peut inclure par leurs clients, le code généré à celui\-ci est fiable, et que le système peut être rapidement mis à jour si les besoins des clients changent.  
  
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] vous permet de créer un langage spécifique au domaine qui a votre propre concepteur graphique et votre propre notation de diagramme, puis utiliser du langage pour générer le code source approprié pour chaque projet.  
  
## Développement de domaine  
 le développement de domaine est le processus d'identifier les éléments de vos applications qui peuvent être modelées en utilisant un langage spécifique au domaine, puis de construire le langage et le déployer des développeurs d'applications.  Les développeurs utilisent du langage spécifique au domaine pour construire des modèles qui sont spécifiques à leurs applications, utilisez les modèles pour générer du code source, puis utilisent code source pour développer des applications.  
  
## Aspects du développement graphique spécifique au domaine  
 Un graphique langage spécifique au domaine doit inclure les fonctionnalités suivantes :  
  
-   Notation  
  
-   modèle de domaine  
  
-   génération d'artefact  
  
-   Sérialisation  
  
-   Intégration à Visual Studio  
  
### Notation  
 Un langage spécifique au domaine doit avoir un ensemble d'éléments relativement court qui peuvent être facilement définis et étendus pour représenter des éléments de domaine.  Une notation se compose des formes, qui représentent les éléments, et les connecteurs, qui représentent les relations entre les éléments, sur une surface de diagramme graphique.  Dans [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], les formes peuvent être étendues et affinées pour représenter les éléments de votre langage spécifique au domaine.  
  
### modèle de domaine  
 Un langage spécifique au domaine doit associer l'ensemble d'éléments et de relations dans une syntaxe logique.  il doit également définir si les combinaisons des éléments et des relations sont valides.  Par exemple, les langages de programmation empêchent généralement l'héritage circulaire, dans lequel la classe est dérivée d'une deuxième classe et la deuxième classe est dérivée de première classe.  Les contraintes peuvent également être utilisées pour exprimer la logique métier, par exemple, une personne ne peut pas être un dépendant de.  [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utilise des contraintes pour exprimer les genres de restrictions que la plupart des langages spécifiques ont besoin.  
  
### génération d'artefact  
 L'un des objectifs principaux d'un langage spécifique au domaine est de générer un artefact, par exemple, le code source, un fichier XML, ou tout autre données utilisable.  En général, une modification du modèle signifie une modification de l'artefact.  Vous pouvez utiliser [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] pour générer des artefacts et les régénérer lorsque vous modifiez le modèle.  
  
### Sérialisation  
 Un langage spécifique au domaine doit être persistant dans une certaine forme qui peut être modifié, enregistré, fermé, puis rechargé.  [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utilise un format XML qui vous permet de définir et personnaliser la façon dont votre langage spécifique au domaine est sérialisé ou persistant.  
  
### Intégration à Visual Studio  
 Étant donné que [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] est hébergé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il étend de nombreuses fenêtres et de contrôles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Elle vous permet également de personnaliser le comportement des commandes de menu, les éléments de boîte à outils, et d'autres éléments de l'interface utilisateur.  
  
 Vous pouvez également créer un adaptateur de modèle de bus pour votre langage spécifique au domaine.  Cet adaptateur vous permet de référencer un modèle et les éléments dans un modèle, et vous permet d'écrire du code qui peut accéder et mettre à jour une instance du langage spécifique à un domaine.  À l'aide de le mécanisme de modèle puissant de bus, vous pouvez écrire des extensions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fonctionnant avec plusieurs modèles.  Vous pouvez également écrire des applications autonomes qui utilisent des modèles.  Pour plus d'informations, consultez [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## Avantages du développement de domaine  
 Un langage spécifique au domaine peut fournir les avantages suivants :  
  
-   Contient des éléments qui correspondent exactement l'espace de problème.  
  
     Contrairement aux langages à usage général, un langage spécifique au domaine se compose des éléments et des relations qui représentent directement la logique de l'espace de problème.  Par exemple, une application de la police d'assurance doit inclure des éléments pour les stratégies et les revendications.  Un langage spécifique au domaine facilite la conception de l'application, et recherche ainsi qu'à des erreurs de logique.  
  
-   Permet aux non\-développeurs et les personnes qui ne connaissent pas le domaine incluent la conception globale.  
  
     En utilisant un langage graphique de domaine, vous pouvez créer une représentation visuelle du domaine afin que les non\-développeurs puissent facilement comprendre la conception de l'application.  
  
-   Le permet de créer un prototype de l'application finale.  
  
     Les développeurs peuvent utiliser le code que leur modèle se produit pour créer une application de prototype qu'ils peuvent indiquer aux clients.  
  
## Le processus de développement spécifique au domaine  
 La plupart des équipes de développement de logiciels qui utilisent des langages spécifiques suivez ces étapes pour créer et utiliser leurs modèles :  
  
-   L'équipe respecte les parties variables du domaine les éléments qui ne changent jamais.  
  
-   Écrivez du code pour développeurs pour les composants et les points fixes d'extension de congé pour les parties variables.  
  
-   Le développeur de logiciels de responsable ou l'architecte crée un langage spécifique au domaine qui incorpore des modèles de design des parties fixes du domaine et l'extension pointe pour les parties variables.  
  
-   Le développeur de logiciels de responsable ou l'architecte déploie le langage spécifique au domaine aux développeurs d'applications différentes que l'équipe produit.  
  
-   chaque développeur crée un modèle qui s'applique à l'application spécifique.