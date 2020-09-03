---
title: Positionnement de la commande, du groupe et de la barre d’outils par défaut | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7fc877332f7db7b27c4a30c23f1ac395a4fc22e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196892"
---
# <a name="default-command-group-and-toolbar-placement"></a>Emplacement de commande, de groupe et de barre d’outils par défaut
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour l’uniformité et la stabilité des produits, l’interface utilisateur affiche certains groupes de commandes par défaut et [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit des définitions pour les commandes et les groupes de commandes. Les VSPackages peuvent également utiliser les commandes et les groupes de commandes standard.  
  
 Les groupes de commandes par défaut se répartissent en trois catégories : les commandes IDE, les commandes du produit et les commandes de l’éditeur.  
  
## <a name="default-ide-commands"></a>Commandes IDE par défaut  
 La barre d’outils IDE par défaut comprend des commandes partagées par tous les produits contenus dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Celles-ci incluent des commandes relatives aux opérations de projet génériques, telles que la commande **Enregistrer** et la commande **Ajouter un élément** . Les VSPackages ne doivent pas ajouter ni soustraire cette barre d’outils, à une exception près : si le produit ou le VSPackage ajoute une nouvelle fenêtre outil, la fenêtre doit être ajoutée à la liste des fenêtres d’outils disponibles dans le menu **affichage** . Les nouveaux produits ou VSPackages peuvent ajouter leur propre barre d’outils.  
  
## <a name="default-product-commands"></a>Commandes de produit par défaut  
 Chaque produit peut fournir à l’IDE sa propre barre d’outils par défaut qui contient des commandes importantes et fréquemment utilisées. Toutefois, il est préférable d’utiliser des menus et des barres d’outils existants chaque fois que cela est possible et de les compléter avec d’autres barres d’outils spécifiques aux tâches si nécessaire.  
  
 Le champ priorité d’une barre d’outils détermine son emplacement de ligne. La priorité zéro place la barre d’outils sur la troisième ligne (ligne 3), sous la barre de menus (ligne 1) et la barre d’outils **standard** (ligne 2). Par conséquent, les autres barres d’outils apparaissent à la ligne (priorité + 3). Les barres d’outils suivantes sont placées sur la même ligne, s’il y a de la place ; dans le cas contraire, ils sont automatiquement déplacés vers la ligne suivante.  
  
## <a name="default-editor-commands"></a>Commandes de l’éditeur par défaut  
 Un VSPackage qui fournit un éditeur personnalisé doit fournir une barre d’outils par défaut qui contient les commandes les plus importantes et les plus fréquemment utilisées dans cet éditeur. La barre d’outils de l’éditeur doit s’afficher lorsque l’éditeur est actif et doit être masqué lorsque l’éditeur n’est pas actif. Cette visibilité est contrôlée dans le `VisibilityConstraints Element` du fichier. vsct.  
  
 Les barres d’outils de l’éditeur doivent être placées sous l’IDE et les barres d’outils du produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, menus et groupes définis par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
