---
title: Processus de transformation du modèle de texte
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b9c65762bbc1fe068889c0420f0dec3d28000130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="the-text-template-transformation-process"></a>Processus de transformation du modèle de texte
Le processus de transformation de modèle de texte prend un fichier de modèle de texte comme entrée et génère un nouveau fichier texte comme sortie. Par exemple, vous pouvez utiliser des modèles de texte pour générer du code Visual Basic ou c#, ou vous pouvez générer un rapport HTML.

 Trois composants font partie de ce processus : le moteur, l’hôte et les processeurs de directive. Le moteur contrôle le processus ; Il interagit avec l’hôte et le processeur de directive pour produire le fichier de sortie. L’hôte fournit toutes les interactions avec l’environnement, comme la localisation des fichiers et des assemblys. Le processeur de directive ajoute des fonctionnalités, telles que la lecture des données à partir d’un fichier XML ou une base de données.

 Le processus de transformation de modèle de texte est effectué en deux étapes. Tout d’abord, le moteur crée une classe temporaire, appelée classe de transformation générée. Cette classe contient le code généré par les directives et les blocs de contrôle. Après cela, le moteur compile et exécute la classe de transformation générée pour produire le fichier de sortie.

## <a name="components"></a>Composants

|Composant|Description|Personnalisable (Oui/non)|
|---------------|-----------------|------------------------------|
|Moteur|Le composant moteur contrôle le processus de transformation de modèle de texte|Non.|
|Hôte|L’hôte est l’interface entre le moteur et l’environnement utilisateur. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est un hôte du processus de transformation de texte.|Oui. Vous pouvez écrire un hôte personnalisé.|
|Processeurs de directive|Processeurs de directive sont des classes qui gèrent les directives de modèles de texte. Vous pouvez utiliser des directives pour fournir des données à un modèle de texte à partir d’une source d’entrée.|Oui. Vous pouvez écrire des processeurs de directive personnalisés|

## <a name="the-engine"></a>Le moteur
 Le moteur reçoit le modèle sous forme de chaîne à partir de l’hôte, qui gère tous les fichiers qui sont utilisés dans le processus de transformation. Il demande alors à l’hôte de rechercher les processeurs de directive personnalisés et d’autres aspects de l’environnement. Ensuite, le moteur compile et exécute la classe de transformation générée. Le moteur retourne le texte généré à l’hôte, qui enregistre normalement le texte dans un fichier.

## <a name="the-host"></a>L’ordinateur hôte
 L’hôte est responsable de tout ce qui est lié à l’environnement en dehors du processus de transformation, notamment les suivantes :

-   Recherche des fichiers texte et binaires demandés par le moteur ou un processeur de directive. L’hôte peut rechercher des répertoires et le global assembly cache pour localiser les assemblys. L’hôte peut localiser le code de processeur de directive personnalisé pour le moteur. L’hôte peut également rechercher et lire des fichiers texte et renvoient leur contenu sous forme de chaînes.

-   Fournit des listes d’assemblys standard et les espaces de noms utilisés par le moteur pour créer la classe de transformation générée.

-   En fournissant le domaine d’application qui est utilisé lorsque le moteur compile et exécute la classe de transformation générée. Un domaine d’application distinct est utilisé afin de protéger l’application hôte à partir d’erreurs dans le code du modèle.

-   Écriture du fichier de sortie généré.

-   Définition de l’extension par défaut pour le fichier de sortie généré.

-   Gestion des erreurs de transformation de modèle de texte. Par exemple, l’hôte peut afficher les erreurs dans l’interface utilisateur ou les écrire dans un fichier. (Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], erreurs sont affichées dans la fenêtre de Message d’erreur.)

-   Si un utilisateur a appelé une directive sans fournir une valeur, en fournissant une valeur de paramètre obligatoire. Le processeur de directive peut spécifier le nom de la directive et le paramètre et demandez à l’hôte pour fournir une valeur par défaut, le cas échéant.

## <a name="directives-and-directive-processors"></a>Directives et des processeurs de Directive
 Une directive est une commande dans votre modèle de texte. Il fournit des paramètres pour le processus de génération. En règle générale, les directives définissent la source et le type du modèle ou d’autres entrées et l’extension de nom de fichier du fichier de sortie.

 Un processeur de directive peut traiter une ou plusieurs directives. Lorsque vous transformez un modèle, vous devez avoir installé un processeur de directive peut traiter les directives de votre modèle.

 Les directives fonctionnent en ajoutant du code dans la classe de transformation générée. Vous appelez des directives à partir d’un modèle de texte et le moteur traite tous les appels de directive lorsqu’il crée la classe de transformation générée. Après avoir appelé une directive avec succès, le reste du code que vous écrivez dans votre modèle de texte peut reposer sur les fonctionnalités offertes par la directive. Par exemple, vous pouvez effectuer l’appel suivant à la `import` directive dans votre modèle :

 `<#@ import namespace="System.Text" #>`

 Le processeur de directive standard la convertit en un `using` instruction dans la classe de transformation générée. Vous pouvez ensuite utiliser le `StringBuilder` classe dans le reste de votre code de modèle sans qualifier comme `System.Text.StringBuilder`.