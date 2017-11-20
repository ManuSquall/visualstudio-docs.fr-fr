---
title: "Par défaut de la commande, le groupe et la sélection élective de la barre d’outils | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5f1ec42408e4fd7d33d9445ae09252fae8d03db
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="default-command-group-and-toolbar-placement"></a>Commande par défaut, le groupe et la sélection élective de la barre d’outils
Pour l’uniformité de produit et de stabilité, l’interface utilisateur affiche certains groupes de commandes par défaut, et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit les définitions pour les commandes et les groupes de commandes. VSPackages peuvent également utiliser les commandes standards et les groupes de commandes.  
  
 Les groupes de commandes par défaut se répartissent en trois catégories : IDE de commandes, les commandes de produits et les commandes de l’éditeur.  
  
## <a name="default-ide-commands"></a>Commandes d’IDE par défaut  
 La barre d’outils IDE par défaut inclut des commandes partagées par tous les produits contenus dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Celles-ci comprennent les commandes relatives aux opérations de projet générique, tel que le **enregistrer** commande et le **ajouter un élément** commande. VSPackages ne devez pas ajouter ou soustraire de cette barre d’outils, à une exception près : si le produit ou un VSPackage ajoute une nouvelle fenêtre outil, alors que la fenêtre doit être ajoutée à la liste des fenêtres Outil disponible sur le **vue** menu. Nouveaux produits ou les VSPackages peuvent ajouter leur propre barre d’outils.  
  
## <a name="default-product-commands"></a>Commandes de produit par défaut  
 Chaque produit peut fournir l’IDE avec sa propre barre d’outils par défaut qui contient importantes et les commandes fréquemment utilisées. Toutefois, il est préférable, pour utiliser existante des menus et barres d’outils, chaque fois que possible et les compléter avec les autres barres d’outils spécifiques à une tâche en fonction des besoins.  
  
 Le champ priorité pour une barre d’outils détermine sa position de ligne. Zéro priorité place la barre d’outils sur la troisième ligne (ligne 3), sous la barre de menus (ligne 1) et le **Standard** la barre d’outils (ligne 2). Par conséquent, les autres barres d’outils apparaissent à la ligne (priorité + 3). Barres d’outils suivants sont placés sur la même ligne, si l’espace ; dans le cas contraire, ils sont automatiquement déplacés vers la ligne suivante.  
  
## <a name="default-editor-commands"></a>Commandes de l’éditeur par défaut  
 Un VSPackage qui fournit un éditeur personnalisé doit fournir une barre d’outils par défaut qui contient les plus importantes et les commandes fréquemment utilisées dans l’éditeur. La barre d’outils de l’éditeur doit apparaître lorsque l’éditeur est actif et qu’il doit être masqué lorsque l’éditeur n’est pas active. Cette visibilité est contrôlée dans le `VisibilityConstraints Element` du fichier .vsct.  
  
 Barres d’outils de l’éditeur doivent être placés au-dessous des barres d’outils de l’IDE et de produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Les groupes, les Menus et commandes définies par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)