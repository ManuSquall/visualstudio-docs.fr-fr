---
title: "The Text Template Transformation Process | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, transformation process"
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 30
---
# The Text Template Transformation Process
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le processus de transformation du modèle de texte accepte un fichier modèle de texte comme entrée et génère un nouveau fichier texte comme sortie.  Par exemple, vous pouvez utiliser des modèles de texte pour générer du code Visual Basic ou C\# ; vous avez également la possibilité de générer un rapport HTML.  
  
 Trois composants participent à ce processus : le moteur, l'hôte et les processeurs de directive.  Le moteur contrôle le processus ; il interagit avec l'hôte et le processeur de directive pour produire le fichier de sortie.  L'hôte assure toutes les interactions avec l'environnement, telles que la recherche des fichiers et des assemblys.  Le processeur de directive ajoute des fonctionnalités, telles que la lecture des données d'un fichier XML ou d'une base de données.  
  
 Le processus de transformation du modèle de texte est exécuté en deux étapes.  Tout d'abord, le moteur crée une classe temporaire, appelée classe de transformation générée.  Cette classe contient le code généré par les directives et les blocs de contrôle.  Ensuite, le moteur compile et exécute la classe de transformation générée pour produire le fichier de sortie.  
  
## Composants  
  
|Composant|Description|Personnalisable \(Oui\/Non\)|  
|---------------|-----------------|----------------------------------|  
|Moteur|Le composant moteur contrôle le processus de transformation du modèle de texte.|Non.|  
|Hôte|L'hôte est l'interface entre le moteur et l'environnement utilisateur.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est un hôte du processus de transformation de texte.|Oui.  Vous pouvez écrire un hôte personnalisé.|  
|Processeurs de directive|Les processeurs de directive sont des classes qui gèrent les directives dans les modèles de texte.  Vous pouvez utiliser des directives pour fournir des données à un modèle de texte à partir d'une source d'entrée.|Oui.  Vous pouvez écrire des processeurs de directive personnalisés.|  
  
## Moteur  
 Le moteur reçoit le modèle sous la forme d'une chaîne provenant de l'hôte, qui gère tous les fichiers utilisés dans le processus de transformation.  Il demande alors à l'hôte de rechercher les processeurs de directive personnalisés et d'autres aspects de l'environnement.  Ensuite, il compile et exécute la classe de transformation générée.  Le moteur retourne le texte généré à l'hôte, qui enregistre normalement le texte dans un fichier.  
  
## Hôte  
 L'hôte est responsable de toutes les opérations liées à l'environnement qui ne font pas partie du processus de transformation. Il s'agit notamment des opérations suivantes :  
  
-   Recherche des fichiers texte et binaires demandés par le moteur ou un processeur de directive.  L'hôte peut effectuer des recherches dans les répertoires et le Global Assembly Cache pour localiser les assemblys.  Il peut rechercher du code de processeur de directive personnalisé pour le moteur.  L'hôte peut également rechercher et lire des fichiers texte, puis retourner leur contenu sous forme de chaînes.  
  
-   Mise à disposition de listes d'espaces de noms et d'assemblys standard que le moteur utilise pour créer la classe de transformation générée.  
  
-   Mise à disposition du domaine d'application qui est utilisé lorsque le moteur compile et exécute la classe de transformation générée.  Un domaine d'application séparé est employé pour protéger l'application hôte contre les erreurs contenues dans le code du modèle.  
  
-   Écriture du fichier de sortie généré.  
  
-   Définition de l'extension par défaut du fichier de sortie généré.  
  
-   Gestion des erreurs de transformation du modèle de texte.  Par exemple, l'hôte peut afficher les erreurs dans l'interface utilisateur ou les écrire dans un fichier.  \(Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], les erreurs sont affichées dans la fenêtre Message d'erreur.\)  
  
-   Mise à disposition d'une valeur de paramètre obligatoire si un utilisateur a appelé une directive sans indiquer de valeur.  Le processeur de directive peut spécifier le nom de la directive et le paramètre, et demander à l'hôte de fournir une valeur par défaut s'il en a une.  
  
## Directives et processeurs de directive  
 Une directive est une commande de votre modèle de texte.  Elle fournit des paramètres au processus de génération.  En général, les directives définissent la source et le type du modèle ou d'une autre entrée, ainsi que l'extension de nom du fichier de sortie.  
  
 Un processeur de directive peut traiter une ou plusieurs directives.  Lorsque vous transformez un modèle, vous devez avoir installé un processeur de directive qui peut traiter les directives du modèle.  
  
 Les directives fonctionnent en ajoutant du code à la classe de transformation générée.  Vous appelez les directives à partir d'un modèle de texte et le moteur traite tous les appels de directive lorsqu'il crée la classe de transformation générée.  Une fois que vous avez appelé avec succès une directive, le reste du code que vous écrivez dans votre modèle de texte peut faire appel aux fonctionnalités qu'elle fournit.  Par exemple, vous pouvez effectuer l'appel suivant à la directive `import` dans votre modèle :  
  
 `<#@ import namespace="System.Text" #>`  
  
 Le processeur de directive standard la convertit en instruction `using` dans la classe de transformation générée.  Vous pouvez ensuite utiliser la classe `StringBuilder` dans le reste du code de votre modèle sans la qualifier comme `System.Text.StringBuilder`.