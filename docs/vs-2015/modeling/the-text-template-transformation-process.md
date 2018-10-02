---
title: Le processus de Transformation de modèle de texte | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c7b39517e5e4c88bbefe6bf378e1dffd3c233872
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505908"
---
# <a name="the-text-template-transformation-process"></a>Processus de transformation du modèle de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [le processus de Transformation de modèle de texte](https://docs.microsoft.com/visualstudio/modeling/the-text-template-transformation-process).  
  
Le processus de transformation de modèle de texte prend un fichier de modèle de texte comme entrée et génère un nouveau fichier texte comme sortie. Par exemple, vous pouvez utiliser des modèles de texte pour générer du code Visual Basic ou c#, ou vous pouvez générer un rapport HTML.  
  
 Trois composants prennent part à ce processus : le moteur, l’hôte et les processeurs de directive. Le moteur contrôle le processus ; Il interagit avec l’hôte et le processeur de directive pour produire le fichier de sortie. L’hôte fournit toutes les interactions avec l’environnement, comme la localisation des fichiers et les assemblys. Le processeur de directive ajoute des fonctionnalités, telles que la lecture des données à partir d’un fichier XML ou une base de données.  
  
 Le processus de transformation de modèle de texte s’effectue en deux étapes. Tout d’abord, le moteur crée une classe temporaire, qui est appelée au sein de la classe de transformation générée. Cette classe contient le code généré par les directives et les blocs de contrôle. Après cela, le moteur compile et exécute la classe de transformation générée pour produire le fichier de sortie.  
  
## <a name="components"></a>Composants  
  
|Composant|Description|Personnalisable (Oui/non)|  
|---------------|-----------------|------------------------------|  
|Moteur|Le composant moteur contrôle le processus de transformation de modèle de texte|Non.|  
|Hôte|L’hôte est l’interface entre le moteur et l’environnement utilisateur. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est un hôte du processus de transformation de texte.|Oui. Vous pouvez écrire un hôte personnalisé.|  
|Processeurs de directive|Processeurs de directive sont des classes qui gèrent les directives de modèles de texte. Vous pouvez utiliser des directives pour fournir des données à un modèle de texte à partir d’une source d’entrée.|Oui. Vous pouvez écrire des processeurs de directive personnalisés|  
  
## <a name="the-engine"></a>Le moteur  
 Le moteur reçoit le modèle sous forme de chaîne à partir de l’hôte, qui gère tous les fichiers qui sont utilisés dans le processus de transformation. Le moteur demande ensuite à l’hôte pour localiser des processeurs de directive personnalisés et d’autres aspects de l’environnement. Ensuite, le moteur compile et exécute la classe de transformation générée. Le moteur retourne le texte généré à l’hôte, qui enregistre normalement le texte dans un fichier.  
  
## <a name="the-host"></a>L’hôte  
 L’hôte est responsable de tout ce qui est lié à l’environnement en dehors du processus de transformation, y compris les éléments suivants :  
  
-   Localisation des fichiers texte et binaires demandés par le moteur ou un processeur de directive. L’hôte peut rechercher des répertoires et le global assembly cache pour localiser les assemblys. Il peut rechercher du code de processeur de directive personnalisé pour le moteur. L’hôte peut également rechercher et lire des fichiers texte et retourner leur contenu sous forme de chaînes.  
  
-   Fournissant des listes d’assemblys standards et d’espaces de noms utilisés par le moteur pour créer la classe de transformation générée.  
  
-   En fournissant le domaine d’application qui est utilisé lorsque le moteur compile et exécute la classe de transformation générée. Un domaine d’application distinct est utilisé afin de protéger l’application hôte des erreurs contenues dans le code du modèle.  
  
-   Écriture du fichier de sortie générée.  
  
-   Définition de l’extension par défaut pour le fichier de sortie généré.  
  
-   Gestion des erreurs de transformation de modèle de texte. Par exemple, l’hôte peut afficher les erreurs dans l’interface utilisateur ou les écrire dans un fichier. (Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], erreurs sont affichées dans la fenêtre de Message d’erreur.)  
  
-   Si un utilisateur a appelé une directive sans fournir une valeur, en fournissant une valeur de paramètre obligatoire. Le processeur de directive peut spécifier le nom de la directive et le paramètre et demander à l’hôte pour fournir une valeur par défaut, le cas échéant.  
  
## <a name="directives-and-directive-processors"></a>Directives et des processeurs de Directive  
 Une directive est une commande dans votre modèle de texte. Il fournit des paramètres pour le processus de génération. Directives définissent généralement la source et le type du modèle ou d’autres entrées et l’extension de nom de fichier du fichier de sortie.  
  
 Un processeur de directive peut traiter une ou plusieurs directives. Lorsque vous transformez un modèle, vous devez avoir installé un processeur de directive peut traiter les directives dans votre modèle.  
  
 Les directives fonctionnent en ajoutant du code dans la classe de transformation générée. Vous appelez des directives à partir d’un modèle de texte et le moteur traite tous les appels de directive lorsqu’il crée la classe de transformation générée. Une fois que vous appelez une directive avec succès, le reste du code que vous écrivez dans votre modèle de texte peut reposer sur les fonctionnalités fournies par la directive. Par exemple, vous pouvez effectuer l’appel suivant à la `import` directive dans votre modèle :  
  
 `<#@ import namespace="System.Text" #>`  
  
 Le processeur de directive standard la convertit en un `using` instruction dans la classe de transformation générée. Vous pouvez ensuite utiliser le `StringBuilder` classe dans le reste de votre code de modèle sans fournir son nom qualifié en tant que `System.Text.StringBuilder`.



