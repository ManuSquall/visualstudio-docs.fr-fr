---
title: Processus de transformation du modèle de texte
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 271d9625ba5c41599af6c92504b3f17a166a2ee7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061774"
---
# <a name="the-text-template-transformation-process"></a>Processus de transformation du modèle de texte
Le processus de transformation de modèle de texte prend un fichier de modèle de texte comme entrée et génère un nouveau fichier texte comme sortie. Par exemple, vous pouvez utiliser des modèles de texte pour générer du code Visual Basic ou c#, ou vous pouvez générer un rapport HTML.

 Trois composants prennent part à ce processus : le moteur, l’hôte et les processeurs de directive. Le moteur contrôle le processus ; Il interagit avec l’hôte et le processeur de directive pour produire le fichier de sortie. L’hôte fournit toutes les interactions avec l’environnement, comme la localisation des fichiers et les assemblys. Le processeur de directive ajoute des fonctionnalités, telles que la lecture des données à partir d’un fichier XML ou une base de données.

 Le processus de transformation de modèle de texte s’effectue en deux étapes. Tout d’abord, le moteur crée une classe temporaire, qui est appelée au sein de la classe de transformation générée. Cette classe contient le code généré par les directives et les blocs de contrôle. Après cela, le moteur compile et exécute la classe de transformation générée pour produire le fichier de sortie.

## <a name="components"></a>Composants

|Composant|Description|Personnalisable (Oui/non)|
|-|-|-|
|Moteur|Le composant moteur contrôle le processus de transformation de modèle de texte|Non.|
|Hôte|L’hôte est l’interface entre le moteur et l’environnement utilisateur. Visual Studio est un hôte du processus de transformation de texte.|Oui. Vous pouvez écrire un hôte personnalisé.|
|Processeurs de directive|Processeurs de directive sont des classes qui gèrent les directives de modèles de texte. Vous pouvez utiliser des directives pour fournir des données à un modèle de texte à partir d’une source d’entrée.|Oui. Vous pouvez écrire des processeurs de directive personnalisés|

## <a name="the-engine"></a>Le moteur
 Le moteur reçoit le modèle sous forme de chaîne à partir de l’hôte, qui gère tous les fichiers qui sont utilisés dans le processus de transformation. Le moteur demande ensuite à l’hôte pour localiser des processeurs de directive personnalisés et d’autres aspects de l’environnement. Ensuite, le moteur compile et exécute la classe de transformation générée. Le moteur retourne le texte généré à l’hôte, qui enregistre normalement le texte dans un fichier.

## <a name="the-host"></a>L’hôte
 L’hôte est responsable de tout ce qui est lié à l’environnement en dehors du processus de transformation, y compris les éléments suivants :

- Localisation des fichiers texte et binaires demandés par le moteur ou un processeur de directive. L’hôte peut rechercher des répertoires et le global assembly cache pour localiser les assemblys. Il peut rechercher du code de processeur de directive personnalisé pour le moteur. L’hôte peut également rechercher et lire des fichiers texte et retourner leur contenu sous forme de chaînes.

- Fournissant des listes d’assemblys standards et d’espaces de noms utilisés par le moteur pour créer la classe de transformation générée.

- En fournissant le domaine d’application qui est utilisé lorsque le moteur compile et exécute la classe de transformation générée. Un domaine d’application distinct est utilisé afin de protéger l’application hôte des erreurs contenues dans le code du modèle.

- Écriture du fichier de sortie générée.

- Définition de l’extension par défaut pour le fichier de sortie généré.

- Gestion des erreurs de transformation de modèle de texte. Par exemple, l’hôte peut afficher les erreurs dans l’interface utilisateur ou les écrire dans un fichier. (Dans Visual Studio, les erreurs sont affichées dans la fenêtre de Message d’erreur).

- Si un utilisateur a appelé une directive sans fournir une valeur, en fournissant une valeur de paramètre obligatoire. Le processeur de directive peut spécifier le nom de la directive et le paramètre et demander à l’hôte pour fournir une valeur par défaut, le cas échéant.

## <a name="directives-and-directive-processors"></a>Directives et des processeurs de Directive
 Une directive est une commande dans votre modèle de texte. Il fournit des paramètres pour le processus de génération. Directives définissent généralement la source et le type du modèle ou d’autres entrées et l’extension de nom de fichier du fichier de sortie.

 Un processeur de directive peut traiter une ou plusieurs directives. Lorsque vous transformez un modèle, vous devez avoir installé un processeur de directive peut traiter les directives dans votre modèle.

 Les directives fonctionnent en ajoutant du code dans la classe de transformation générée. Vous appelez des directives à partir d’un modèle de texte et le moteur traite tous les appels de directive lorsqu’il crée la classe de transformation générée. Une fois que vous appelez une directive avec succès, le reste du code que vous écrivez dans votre modèle de texte peut reposer sur les fonctionnalités fournies par la directive. Par exemple, vous pouvez effectuer l’appel suivant à la `import` directive dans votre modèle :

 `<#@ import namespace="System.Text" #>`

 Le processeur de directive standard la convertit en un `using` instruction dans la classe de transformation générée. Vous pouvez ensuite utiliser le `StringBuilder` classe dans le reste de votre code de modèle sans fournir son nom qualifié en tant que `System.Text.StringBuilder`.