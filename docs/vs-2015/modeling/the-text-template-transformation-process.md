---
title: Processus de transformation du modèle de texte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7322724b2118cb8b844262696a6e7cbd91a74e9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658506"
---
# <a name="the-text-template-transformation-process"></a>Processus de transformation du modèle de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le processus de transformation de modèle de texte prend un fichier de modèle de texte comme entrée et génère un nouveau fichier texte comme sortie. Par exemple, vous pouvez utiliser des modèles de texte pour générer C# Visual Basic ou du code, ou vous pouvez générer un rapport HTML.

 Trois composants participent à ce processus : le moteur, l’hôte et les processeurs de directive. Le moteur contrôle le processus ; Il interagit avec l’hôte et le processeur de directive pour produire le fichier de sortie. L’hôte fournit toute interaction avec l’environnement, telle que la localisation des fichiers et des assemblys. Le processeur de directive ajoute des fonctionnalités, telles que la lecture de données à partir d’un fichier XML ou d’une base de données.

 Le processus de transformation de modèle de texte s’effectue en deux étapes. Tout d’abord, le moteur crée une classe temporaire, appelée classe de transformation générée. Cette classe contient le code généré par les directives et les blocs de contrôle. Après cela, le moteur compile et exécute la classe de transformation générée pour produire le fichier de sortie.

## <a name="components"></a>Composants

|Composant|Description|Personnalisable (oui/non)|
|---------------|-----------------|------------------------------|
|Rotation|Le composant moteur contrôle le processus de transformation de modèle de texte.|Non.|
|Hôte|L’hôte est l’interface entre le moteur et l’environnement utilisateur. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est un hôte du processus de transformation de texte.|Oui. Vous pouvez écrire un hôte personnalisé.|
|Processeurs de directive|Les processeurs de directive sont des classes qui gèrent les directives dans les modèles de texte. Vous pouvez utiliser des directives pour fournir des données à un modèle de texte à partir d’une source d’entrée.|Oui. Vous pouvez écrire des processeurs de directive personnalisés|

## <a name="the-engine"></a>Le moteur
 Le moteur reçoit le modèle en tant que chaîne à partir de l’hôte, qui gère tous les fichiers utilisés dans le processus de transformation. Le moteur demande ensuite à l’hôte de localiser tous les processeurs de directive personnalisés et d’autres aspects de l’environnement. Le moteur compile ensuite et exécute la classe de transformation générée. Le moteur retourne le texte généré à l’hôte, ce qui enregistre normalement le texte dans un fichier.

## <a name="the-host"></a>L’hôte
 L’hôte est responsable de tout ce qui est en relation avec l’environnement en dehors du processus de transformation, y compris les éléments suivants :

- Recherche de fichiers texte et binaires demandés par le moteur ou un processeur de directive. L’hôte peut rechercher des répertoires et le Global Assembly Cache pour localiser les assemblys. L’hôte peut localiser le code du processeur de directive personnalisé pour le moteur. L’hôte peut également rechercher et lire des fichiers texte et retourner leur contenu sous forme de chaînes.

- Fournit des listes d’assemblys standard et d’espaces de noms utilisés par le moteur pour créer la classe de transformation générée.

- Fournir le domaine d’application utilisé lorsque le moteur compile et exécute la classe de transformation générée. Un domaine d’application distinct est utilisé pour protéger l’application hôte des erreurs dans le code du modèle.

- Écriture du fichier de sortie généré.

- Définition de l’extension par défaut pour le fichier de sortie généré.

- Gestion des erreurs de transformation du modèle de texte. Par exemple, l’hôte peut afficher les erreurs dans l’interface utilisateur ou les écrire dans un fichier. (Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], les erreurs sont affichées dans la fenêtre de message d’erreur.)

- Fournir une valeur de paramètre obligatoire si un utilisateur a appelé une directive sans fournir de valeur. Le processeur de directive peut spécifier le nom de la directive et le paramètre et demander à l’hôte de fournir une valeur par défaut s’il en a un.

## <a name="directives-and-directive-processors"></a>Directives et processeurs de directive
 Une directive est une commande dans votre modèle de texte. Il fournit des paramètres au processus de génération. En général, les directives définissent la source et le type du modèle ou d’une autre entrée, ainsi que l’extension du nom de fichier du fichier de sortie.

 Un processeur de directive peut traiter une ou plusieurs directives. Lorsque vous transformez un modèle, vous devez avoir installé un processeur de directive qui peut gérer les directives de votre modèle.

 Les directives fonctionnent en ajoutant du code dans la classe de transformation générée. Vous appelez des directives à partir d’un modèle de texte, et le moteur traite tous les appels de directive lorsqu’il crée la classe de transformation générée. Une fois que vous avez correctement appelé une directive, le reste du code que vous écrivez dans votre modèle de texte peut reposer sur les fonctionnalités fournies par la directive. Par exemple, vous pouvez effectuer l’appel suivant à la directive `import` dans votre modèle :

 `<#@ import namespace="System.Text" #>`

 Le processeur de directive standard convertit ce en une instruction `using` dans la classe de transformation générée. Vous pouvez ensuite utiliser la classe `StringBuilder` dans le reste de votre code de modèle sans l’qualifier comme `System.Text.StringBuilder`.
