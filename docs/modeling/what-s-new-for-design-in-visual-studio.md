---
title: "Quelles sont les nouveautés de conception dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 32
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17bc5792d4fa9fac0b97705e61372dcc884c82a2
ms.openlocfilehash: 2704914ab8607e0a7442a45589e6a6cab08b7338
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-for-design-in-visual-studio"></a>Quelles sont les nouveautés de conception dans Visual Studio

## <a name="live-dependency-validation"></a>Validation de dépendance dynamique

Suppression des dépendances indésirables est une partie importante de la gestion de la dette technique.
Validation en direct de dépendances est maintenant inclus, fournissant des informations précises sur les problèmes et bénéficiant pleinement parti des nouvelles fonctionnalités dans la liste d’erreurs et l’éditeur.

![Validation de dépendance dynamique en action](media/dep-validation-whatsnew-01.png)

L’expérience de création a changé pour effectuer la validation de dépendance plus visibles et plus accessibles, modification de la terminologie à partir de « Diagramme de couche » à « Diagramme de dépendance ».

Le **Architecture** menu contient à présent une commande pour créer directement un diagramme de dépendances :

![Élément de dépendance en direct sur le menu d’Architecture](media/dep-validation-whatsnew-02.png)

... et les noms des propriétés d’une couche dans un diagramme de dépendances et leurs descriptions, ont été modifiés pour les rendre plus significatives :

![Noms de propriété de dépendance Live mis à jour](media/dep-validation-whatsnew-03.png)

Vous consultez maintenant l’impact de vos modifications immédiatement dans les résultats d’analyse du code en cours dans la solution chaque fois que vous enregistrez le diagramme. Vous n’êtes pas obligé d’attendre plus longtemps l’achèvement de la commande « Dépendances de validation ».

Pour plus d’informations, consultez [ce billet de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/). 
 
## <a name="uml-designers-have-been-removed"></a>Concepteurs UML ont été supprimés.

Les concepteurs UML ont été supprimés de cette version de Visual Studio Enterprise.

* Diagrammes UML sont maintenant présentés en tant que fichiers XML
* L’Explorateur de modèles UML n’existe plus
* Les références ne sont plus utilisés pour la validation de dépendance de projet de modélisation
* Le nœud « Références de couche » dans l’Explorateur de solutions n’est plus affiché
* L’action de génération « Valider » sur un diagramme de dépendances (Layer) n’est plus utilisée, la tâche de génération a été supprimée. 
* La structure de projet est conservée pour l’aller-retour entre les versions
* Vous pouvez toujours ouvrir, créer, modifier et enregistrer un diagramme de dépendances (couche) au format XML
* Les éléments de travail TFS liés à un diagramme de dépendances (couche) ne sont pas accessibles sur l’aire de conception
* Liaison arrière à partir de DSL ou une couche est plus pris en charge 
* Extensibilité UML dans le Kit de développement logiciel de modélisation n’est plus pris en charge.

Toutefois, la prise en charge pour visualiser l’architecture de code .NET et C++ est disponible via [cartes de code](map-dependencies-across-your-solutions.md)et les améliorations significatives pour la validation de dépendance décrites ci-dessus.

Si vous êtes un utilisateur significatif des concepteurs UML, vous pouvez continuer à utiliser Visual Studio 2015 ou une version antérieure alors que vous choisissez un autre outil pour vos besoins UML.

Pour plus d’informations, consultez [ce billet de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/). 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>Prise en charge des versions pour les outils d'architecture et de modélisation  

Visual Studio est disponible dans plusieurs versions. Toutes les versions ne prennent pas en charge les outils d'architecture et de modélisation. Le tableau ci-après décrit la disponibilité de chaque outil.  
  
|**Fonctionnalité**|**Entreprise**|**Professionnel**|**Community**|**Express**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**Cartes de code**|Oui|Voir la Remarque (1)|-|-|  
|**Diagrammes de dépendance**|Oui|Voir la Remarque (2)|Voir la Remarque (2)|-|  
|**Graphiques orientés** (diagrammes DGML)|Oui|Oui|Oui|-|  
|**Clone de code**|Oui|-|-|-|  
  
Remarque (1) : prend en charge uniquement la lecture de cartes de code, le filtrage de cartes de code, l’ajout de nouveaux nœuds génériques et la création d’un graphique orienté à partir d’une sélection.

Remarque (2) : Prend uniquement en charge la lecture des diagrammes de dépendance.

